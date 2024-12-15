# Distributed_System_Assignment
# Lamport Clock

A **Lamport Clock** is a logical clock used in distributed systems to establish a partial ordering of events. It helps synchronize events in systems where there is no shared global clock, and processes communicate by exchanging messages.

## Mechanism

The mechanism of a Lamport Clock works as follows:

1. Each process maintains a local counter, initialized to zero.
2. Before executing an event, the process increments its counter by 1.
3. When a process sends a message, it includes its current counter value.
4. Upon receiving a message, the recipient updates its counter to be the maximum of its current counter and the counter received in the message, then increments it by 1.
Here are the **Clock Condition** and **IR Rules** of Lamport Clock presented in mathematical notations:

### Clock Condition
If an event \( a \) happens before another event \( b \) in a distributed system (denoted \( a \rightarrow b \)), then their timestamps satisfy the following condition:
\[
C(a) < C(b) \quad \text{if} \quad a \rightarrow b
\]

### Increment Rule (IR1)
When a process performs an event \( e_i \), it increments its local logical clock as:
\[
C(e_i) = C(e_{i-1}) + 1
\]
where \( e_{i-1} \) is the previous event in the same process.

### Receive Rule (IR2)
When a process receives a message with timestamp \( C_m \), it updates its logical clock as:
\[
C(e_r) = \max(C(e_r-1), C_m) + 1
\]
where:
- \( C(e_r-1) \): the process's clock before receiving the message.
- \( C_m \): the timestamp attached to the received message.
- \( C(e_r) \): the updated clock value after processing the message.

Let me know if you need further clarification or additional details!
## Key Features
- Establishes a **partial ordering** of events in distributed systems.
- Ensures consistent ordering of events across processes.
- Does **not capture causal relationships** comprehensively (for causal relationships, see **Vector Clocks**).

## Use Cases
Lamport Clocks are widely used in distributed systems to:
- Resolve conflicts in distributed databases.
- Maintain consistency in distributed applications.

## References
For more information, refer to:
- [Leslie Lamport's Original Paper on Logical Clocks](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)


