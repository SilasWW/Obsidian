#Disys 
## Idempotence:
An operation is idempotent if performing it multiple times has the same effect as performing it once. This doesn't mean that the operation does nothing; rather, it means that after the first application, subsequent applications do not change the state further.

### Patterns:
Generally something is idempotent if it sets a state to a specific value, rather than changes the state by a specific value, like by incrementation.

*Example:*
#### Idempotent Operation

**Setting a Specific Value:**

- **Operation**: "Set the account balance to $1000."
- **Explanation**: No matter how many times this operation is performed, the account balance will be $1000. The first time it's executed, the balance is set to $1000. If you repeat the operation, the balance remains at $1000. The state of the account balance doesn't change after the first application.
- **Context**: This can be likened to an HTTP PUT request in a web service where you're updating a resource to have a specific state.

#### Non-Idempotent Operation

**Incrementing a Value:**

- **Operation**: "Add $100 to the account balance."
- **Explanation**: This operation changes the state each time it's executed. If the account balance is initially $1000, after the operation is executed once, it becomes $1100. If you perform the operation again, the balance becomes $1200, and so on. Each execution changes the state.
- **Context**: This is similar to an HTTP POST request where you're adding a new resource or changing the state in a way that varies with each request.