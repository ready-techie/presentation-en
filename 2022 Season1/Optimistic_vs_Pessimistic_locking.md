## How to prevent DB conflict

first. Make lock when we access some row in table. no one can access this row, when lock is working.

second. when modifying, specify on the modified row. so no one can modify this row under the same condition

### Pessimistic locking (first condition)

[Pessimistic Locking](http://en.wikipedia.org/wiki/Lock_(database)) is when you lock the row for your exclusive use until you have finished with it.

It has much better integrity than optimistic locking but requires you to be careful with your application design to avoid Deadlocks.

**process**

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc3291c97-32a4-4a3e-97f1-7bc25302c030%2FUntitled.png?table=block&id=78cdb16d-1cb2-4a02-81b3-6ea6b3e0ee25&spaceId=89ee5b3a-d258-4b8e-b2c8-d73f59ac55f7&width=2000&userId=005ba5d1-5f2d-4bcd-85e6-46030028e334&cache=v2)

1. **transaction 1** read id 2
2. **transaction 2** read id 2
3. **transaction 2** update id 2
    1. blocking. because transaction 1 is locking this row. so transaction 2 is waiting = block.
4. **transaction 1** commit
5. **transaction 2** update complete

### Optimistic locking (second condition)

[Optimistic Locking](http://en.wikipedia.org/wiki/Optimistic_locking) is a strategy when you read a row, take note of a version number and check that the version hasn't changed before you write the row back. 

When you write the row back you filter the update on the version to make sure it's atomic. (i.e. hasn't been updated between when you check the version and write the row to the disk) 

update the version in one hit.

**process**

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe096d4f8-7a2f-4767-b3cb-2589a8d1b3bf%2FUntitled.png?table=block&id=b01adcb3-cf4f-4ddd-8b7e-6a94faaa4895&spaceId=89ee5b3a-d258-4b8e-b2c8-d73f59ac55f7&width=2000&userId=005ba5d1-5f2d-4bcd-85e6-46030028e334&cache=v2)

1. **transaction 1** read id 2
2. **transaction 2** read id 2
3. **transaction 2** update id 2
4. **transaction 1** update id 2
    1. exception! because this row already updated. so it can not hit this row’s version.
    

### how can solve this case?

umm... solve the conflict yourself in runtime..

```java
public Person someUpdate(Person person, Person newPerson) {
	for (int i = 0; i < RETRY_COUNT; i ++) {
		try {
			dao.update(person, newPerson);
		} catch(Exception e) {
			person = dao.fetch(person);
		}
	}

	throw new Exception();
}
```

### best case about each lock

A : We need only performance!! → Optimistic

→ when many user use some table. toss........

B : this table has a lot of conflict.

→ hmm... use Optimistic. if you have a lot of money.

~~→ Amazon DynamoDB ensures consistent latency.~~

~~→ it does not ensure your money.~~

C : Atomicity is really important in this table. → Pessimistic

→ with high level locking. 

D : solving conflict process is so annoying. → Pessimistic

→ either succeed or fail. ~~use JPA..~~

there is not good answer. there is just the best practice.. 🥲
