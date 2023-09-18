# Transaction Control

In Database transactions mainly we have four properties called ACID.

- Atomicity
- Consistency
- Isolation
- Durability


## Atomicity

Atomicity says, either all perform all the operation that are included in the transaction
successfully, or no operation performed at all.


## Consistency

Consistency says, data will be in consistent state after performing all the operation
of a single transaction.

Ex:-


## Isolation

Each transaction executes in an isolated environment, no transaction do not know
about the other running parallel transaction.

## Durability

Durability says, once the data is persisted it will be stored permanently, until someone
does not remove. Means we can run the database operation on this data forever.

