# Modul 8 Reflection
**Salma Kurnia Dewi (2206026681)**

## What is `amqp`?
   AMQP, an acronym for Advanced Messaging Queuing Protocol, is a standard design for message exchange that supports efficiency in determining the process of message exchange in a wide variety of applications or data communication. 
   This protocol is used for message exchange between different applications or organizations, allowing applications to communicate asynchronously.
   The implementation of AMQP typically involves three main elements: Publisher, the application that sends messages; Broker, the intermediary for messages sent between the publisher and the recipient; and Customer, the recipient of the message. 
   Thus, AMQP facilitates efficient and effective communication across various applications and organizations.

## What does `guest:guest@localhost:5672` mean?
   `guest:guest@localhost:5672` is a URI (Uniform Resource Identifier) used to specify the address of an AMQP broker.
    In this string, the first `guest` refers to the username used for authentication to the broker, while the second `guest` is the password used for the same purpose. 
    The `localhost:5672` part indicates the host address and port used for connection to the AMQP broker.
    Here, `localhost` refers to the local address of the server running on the same machine, and `5672` is the default port number used by the AMQP server. Therefore, this string represents the standard URI format for connection to an AMQP server.

## Simulation slow subscriber
<img src ="img/spikes.png">

   In a slow subscriber simulation, when the `cargo run` command is executed several times in quick succession on the publisher, there is an increase in queued messages.
   This is due to the delay in the subscriber receiving messages from the publisher, simulated through  `thread::sleep`. As a result, messages from the publisher pile up in the queue until the subscriber can receive them.
   This situation differs when execution is performed without sleep. In that case, there is a spike in the queued message graph because the `cargo run` command is executed quickly on the publisher, so the sent messages must be stored in the queue before they can be processed by the subscriber.

## “Reflection and Running at least three subscribers
<img src = "img/Untitled.png">
<img src = "img/Screenshot 2024-04-24 172244.png">

   When executing the `cargo run` command, the execution of all sent messages is divided among the three subscribers. Even though it's executed with sleep, no messages enter the queue, as seen from the queued messages graph. This happens because the messages have been processed by three different subscribers, so the messages no longer need to queue up for execution.