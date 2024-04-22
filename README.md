# Tutorial-8

### Reflection
1. What is **amqp**? <br>
*AMQP, or Advanced Message Queuing Protocol, is an open standard application layer protocol for message-oriented middleware, commonly used to build messaging systems. AMQP enables various applications to communicate with each other by exchanging messages efficiently.*

2. What does `guest:guest@localhost:5672` means? what is the first **quest**, and what is the second **guest**, and what is **localhost:5672** is for? <br>
    - The string `guest:guest@localhost:5672` is a connection string for an AMQP server.

    - `guest:guest` represents the username and password for authentication on the server. In this case, both the username and password are "guest". In many default configurations of message brokers like RabbitMQ, both the default username and password are "guest". However, in production environments, it's highly recommended to change these default credentials for security reasons.

    - `@localhost:5672`specifies the host and port. "localhost" refers to the local machine, meaning that the message broker (RabbitMQ) is running on the same machine where this code is executed. Port 5672 is the default port used by RabbitMQ for AMQP communication.