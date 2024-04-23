# Reflection 1
a. what is amqp?

AMQP stands for Advanced Message Queuing Protocol. It's a way for different computer programs to send messages to each other without needing to connect directly. This protocol defines a set of rules for how messages should be formatted and exchanged between systems. 

b. what it means? guest:guest@localhost:5672

- The first "guest" is like a username we use to log into a website.

- The second "guest" is like a password that goes with the username.

- localhost:5672 specifies the network address and port on which the AMQP server is running:
  
&emsp; • localhost indicates that the server is hosted on the same computer as the client software.

&emsp; • 5672 is the standard port number used for non-encrypted communication with an AMQP server.


This string is commonly used in configurations and scripts to establish a connection to an AMQP server with default credentials and settings.

# Slow Subscriber
![Screenshot 2024-04-24 at 02 35 51](https://github.com/tvadhisti/module8-subscriber/assets/127074983/25bc23d0-bcd4-4ca2-9324-f17eb7100a6f)

![Screenshot 2024-04-24 at 02 36 08](https://github.com/tvadhisti/module8-subscriber/assets/127074983/a2120d86-c722-42c1-88fb-3c1564447eb9)

When I ran my publisher three times, it sent out a total of 15 messages to the queue. However, my subscriber adds a delay of one second for each message it processes. Because of this delay, the subscriber hadn’t finished processing all the messages by the time I checked the queue, which resulted in a total of 11 unacknowledged messages. These are messages that have been received by the subscriber but are still waiting to be processed.
