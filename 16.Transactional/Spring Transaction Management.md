## Transaction Isolation

reference: https://www.youtube.com/watch?v=7rNiIavYB2w
### Types
	1. Repeatable read 
	2. Read uncommitted
	3. Read committed
	4. Serializable
### Repeatable read 
https://youtu.be/7rNiIavYB2w?t=960

### Read uncommitted
https://youtu.be/7rNiIavYB2w?t=1465

it has dirty read problem

### Read committed
it solves dirty read problem in Read uncommitted
watch this for explanation: https://youtu.be/7rNiIavYB2w?t=2298
But it creates a new problem ie Non Repeatable Read
what is Non Repeatable Read - https://youtu.be/7rNiIavYB2w?t=2636
Non Repeatable Read problem is solved by Repeatable Read

### Repeatable Read (visiting again)
it solves Non Repeatable Read problem
watch this : https://youtu.be/7rNiIavYB2w?t=2823
### Useful reads:

- ****Dirty Read -**** A Dirty read is a situation when a transaction reads data that has not yet been committed. ****For example****, Let's say transaction 1 updates a row and leaves it uncommitted, meanwhile, Transaction 2 reads the updated row. If transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed.
- ****Non Repeatable read -**** Non-repeatable reads are when your transaction reads committed **UPDATES** from another transaction. The same row now has different values than it did when your transaction began.
-  ****Phantom reads -**** are similar to Non Repeatable read but when reading from committed **INSERTS** and/or **DELETES** from another transaction. There are new rows or rows that have disappeared since you began the transaction.

![[Pasted image 20250728212625.png]]
