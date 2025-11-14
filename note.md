# Recovery System

## Failure Classification

1.) Transaction Failure
	-Logical Errors: The transaction cannot complete due to some internal error condition
	-System Errors: The database system must terminate an active transaction due to an error condition(Deadlock).

2.) System Crash: A power failure or other hardware or software failure causes the system to crash
	- Fail-Stop assumption: non-volatile storage contents are assumed to not be corrupted by system crash
		-Database systems have numerous integrity checks to prevent corruption of disk data

3.) Disk Failure: A head crash or similar disk failure destroys all or part of disk storage
	-Destruction is assumed to be detectable: disk drives use checksums to detect failures

## Recovery Algorithms

--> Consider Transaction Ti that transfers 50 from account A to account B
	- Two updates: Subtract 50 from A and add 50 to B
--> Transaction Ti requires updates to A and B to be output to the database.
	- A failure may occur after on of these modifications have been made but before both of them are made.
	- Modifying the database without ensuring that the transaction will commit may leave the database in an inconsistent state.
	- Not modifying the database may result in lost updates if failure occurs just after transaction commits

--> Recovery Algorithms have two parts
	1.) Actions taken during normal transaction processing to ensure enough information exists to recover from failures
	2.) Actions taken after a failure to recover the database contents to a state that ensures atomicity, consistency, and durability.


## Data Access

--> Physical blocks are those blocks residing on the disk
--> Buffer block are the blocks residing temporarily in main memory.
--> Block movements between disk and main memory are initiated through the following two operations
	1.) input(b) transfers the physical block B to main memory
	2.) output(b) transfers the buffer block B to the disk and replaces the appropriate physical block there.

--> We assume for simplicity, that each data item fits in, and is stored inside, a single block.

--> Each transaction Ti has its private work-area in which local copies of all data items accessed and updated by it are kept.
	- Ti's local copy of a data item X is called Xi

--> Transferring data items between system buffer blocks and its private work-area done by:
	-read(X) assigns value of data item X to local variable Xi
	-write(x) assigns the value of local variable Xi to data item X in the buffer block.
	- Note: output(Bx) need not immediately follow write(X), system can perform the output operation when it deems fit.

--> Transactions
	1.) Must perform read(X) before accessing X for the first time (Subsequent reads can be from local copy)
	2.) write(X) can be executed at any time before the transaction commits.

## Recovery and Atomicity

--> To ensure atomicity despite failures, we first output information describing the modifications to stable storage without modifying the database itself.

--> We study *log-based recovery mechanisms* in detail
	1.) We first present key concepts
	2.) And then present the actual recovery algorithms

--> Less used alternative: *Shadow-copy* and *Shadow-paging* (refer to book for more details)


## Log-Based Recovery

--> A log is kept on Stable storage
	- The log is a sequence of log records, and maintains a record of update activities on the database.

--> When Transaction Ti sstarts, it registers itself by writing a <Ti start> log record
		<Ti,X,V1,V2>
	is written, where V1 is the value of X before the write and V2 is the value to be written to X.

--> When Ti finishes, the last statement, the log record <Ti commit> is written

--> Two approaches using logs
	1.) Deferred database modification
	2.) Immediate database modification


## Immediate Database Modification

--> The *Immediate-modification* scheme allows updates of an uncommitted transaction to be made to the buffer, or the disk itself, before the transaction commits.

--> Update log record must be written before database item is written
	- We assume that the log record is output directly to stable storage
	- (Will see later that how to postpone log record output to some extent)

--> Output of updated blocks to stable storage can take place at any time before or after transaction commit.

--> Order in which blocks are output can be different from the order in which they are written

--> The *deferred-modification* scheme performs updates to buffer/disk only at the time of transaction commit
	1.) Simplifies some aspect of recovery
	2.) Has overhead of storing local copy


## Transaction Commit
--> A transaction is said to have committed when it commit log record is output to stable storage
	- All previous log records of the transaction must have been output already

--> Writes performed by a transaction may still be in the buffer when the transaction commits, and may be the output later.

## Concurrency Control and Recovery
--> With concurrent transaction, all transactions share a single disk buffer and a single log.
	- A buffer block can have data items updated by one or more transactions

--> We assume that if a transaction Ti has modified an item no other transaction can modify the same item until Ti has committed or aborted
	- i.e the updates of uncommitted transactions should not be visible to other transactions
		- Otherwise how to perfrom undo if T1 updates A, then T2 updates A and commits and finally T1 has to abort.

	- Can be ensured by obtaining exclusive locks on updated items and holding the locks till the end of transaction( Strict two-phase locking)

--> Log records of diff transactions may be interspersed in the log.

## Undo and Redo Operations

--> Undo of a log record <Ti,Xi,V1,V2> Writes the old value V1 to X.
--> Redo of a log record writes the new value V2 to X
--> Undo and Redo of Transactions
	1.) undo(Ti) restores the value of all data items updated by Ti to their old values, going backwards from the last log record for Ti.
		-Each time a data item X is restored to its old value V a special log record <Ti,X,V> is written out.
		- When undo of a transaction is complete, a log record <Ti abort> is written out.
	2.) redo(Ti) sets the value of all data items update by Ti to the new values, going forward from the first log record for Ti
		- No logging is done in this case.


## Undo and Redo on recovering from Failure
--> When recovering after failure:
	- Transaction Ti needs to be undone if the log
		1.) Contains the record <Ti start>
		2.) but does not contain a commit or abort record.
	- Transaction Ti needs to be redone if:
		1.) Contains the start record
		2.) Contains the commit or abort record

--> Note that if the transaction Ti was undone earlier and the abort record was written to the log, and then a failure occurs, on recovery from failure Ti is redone.
	- Such a redo redoes all the original actions including the steps that restored old values.
	- Seems wasteful, but simplifies recovery greatly.

## Repeating History
--> If a transaction T1 updates A from 10 to 20 and then decides to abort and undoes the action via logs, on occurrence of a system failure, the entire transaction will be redone. This includes updating A, undoing it and then aborting.

-->It is simpler and robust: recovery just replays log records (redo) for committed/finished transactions and undoes in-progress transactions according to the log. The recovery logic does not need to reason about which changes were applied to disk before the crash; it replays from the log and achieves a correct on-disk state.

--> It does waste some disk space

## Checkpoints
--> Redoing/Undoing all transaction recorded in the log can be very slow.
	- Processing the entire log is time-consuming if the system has run for a long time.
	- We might unnecessarily redo transactions which have already output their updates to the database.

--> Streamline recover Procedure by periodically performing *checkpointing*
	1.) output all log records currently residing in main memory onto stable storage.
	2.) Output all modified buffer blocks to the disk.
	3.) Write a log record <checkpoint L> onto stable storage where L is a list of all transactions active at the time of checkpoint.
	4.) All updates are stopped while doing checkpointing

--> During recovery we need to consider only the most recent transaction Ti that started before the checkpoint, and transactions that started after Ti.
	1.) Scan backwards from end of log to find the most recent checkpoint record
	2.) Only transactions that are in L or started after the checkpoint need to be redone or undone.
	3.) Transactions that committed or aborted before the checkpoint already have all their updates output to stable storage.

--> Some earlier part of the log may be needed for undo operations
	1.) Continue scanning backwards till a record <Ti start> i found for every transaction in L
	2.) Parts of log prior to earliest <Ti start> record above are not needed for recovery and can be erased whenever desired.



