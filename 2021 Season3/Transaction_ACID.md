# What is Transaction?
- A group of task
- In database, a group of task that changes the database state
    
    ![Untitled](https://limm-jk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1eb077e8-5d1f-4bba-ad5f-33c13bc5cea0%2FUntitled.png?table=block&id=0443e89a-e8ba-46e4-ac26-125d23b075c9&spaceId=89ee5b3a-d258-4b8e-b2c8-d73f59ac55f7&width=750&userId=&cache=v2)
    

# ACID

![Untitled](https://limm-jk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F05c7e49f-cb53-4d63-bd8e-cc8d7799b6ce%2FUntitled.png?table=block&id=78162e12-04d6-4d5b-afc0-dfe9181d7d5c&spaceId=89ee5b3a-d258-4b8e-b2c8-d73f59ac55f7&width=1750&userId=&cache=v2)

ACID is an acronym that refers to the group of 4 properties that define a transaction: **Atomicity**, **Consistency**, **Reliability**, and **Durability**.

### Atomicity

- A transaction (to read, write, update or delete data) is treated as a single group.
- So, all the changes are performed, or none of them are.

### Consistency

- Data is in a consistent state when a transaction starts and when it ends.
- Transactions only make changes to tables in predefined, predictable ways.
- Consistency ensures that corruption or errors in your data do not create unintended consequences for the integrity of your table.

### Isolation

- Multiple users are reading and writing from the same table all at once, isolation of their transactions ensures that the concurrent transactions don’t interfere with or affect one another.
- As a result, transactions that run concurrently appear to be serialized.

### **Durability**

- After a transaction successfully completes, changes to data persist and are not undone, even in the event of a system failure.

# **Why are ACID transactions a good thing to have?**

- Ensure the highest data reliability and integrity.
- Ensure that your data never falls into an inconsistent state because of an operation that partially completes.
