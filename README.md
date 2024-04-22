# Tutorial-8

### Reflection
1. What is **amqp**? <br>
*AMQP, or Advanced Message Queuing Protocol, is an open standard application layer protocol for message-oriented middleware, commonly used to build messaging systems. AMQP enables various applications to communicate with each other by exchanging messages efficiently.*

2. What does `guest:guest@localhost:5672` means? what is the first **quest**, and what is the second **guest**, and what is **localhost:5672** is for? <br>
    - *The string `guest:guest@localhost:5672` is a connection string for an AMQP server.*

    - *`guest:guest` represents the username and password for authentication on the server. In this case, both the username and password are "guest". In many default configurations of message brokers like RabbitMQ, both the default username and password are "guest". However, in production environments, it's highly recommended to change these default credentials for security reasons.*

    - *`@localhost:5672`specifies the host and port. "localhost" refers to the local machine, meaning that the message broker (RabbitMQ) is running on the same machine where this code is executed. Port 5672 is the default port used by RabbitMQ for AMQP communication.*

    ![alt text](assets/images/subscriber-1.jpg)

    *The RabbitMQ interface screenshot when I repeatedly ran `cargo run` on the publisher after implementing threading. Here, it can be seen that the queue reached 15 because I ran `cargo run` 3 times. resulting in a queue of 5 for each `cargo run`. We know that each `cargo run` sends 5 data, hence there is a queue of 15 data.*

    ![alt text](assets/images/subscriber-2.jpg)

    *Screenshot when I ran `cargo run` 4 times on the publisher and `cargo run` 3 times on different consoles on the subscriber. It can be seen that the spike in the message queue decreases, indicating it's faster than before because the requests received in the queue will be distributed to 3 subscribers.*

    *There are several improvements that can be made to this code:*

    - *Avoid using `unwrap()` because using `unwrap()` in production code is not recommended as it can cause the program to panic if Result is Err. Instead, we can elegantly handle errors using match or if let.*

    - *Use constants for repeated strings because if we have a string that is used multiple times (such as `amqp://guest:guest@localhost:5672`), it's better to define it as a constant at the top of the file.*