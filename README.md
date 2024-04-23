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

I ran the publisher code three times, which sent out 15 messages. The subscriber code processes each message with a one second delay. This delay simulates a slow subscriber. Because the subscriber is slow, it doesn't keep up with the incoming messages. By the time I looked at the RabbitMQ, there were 11 unacknowledged messages. These messages are in the queue waiting to be processed by the subscriber. The buildup occurs because the subscriber is processing messages slower than the rate at which they're being published.

#  Running at least three subscribers
![Screenshot 2024-04-24 at 03 16 49](https://github.com/tvadhisti/module8-subscriber/assets/127074983/b36db61f-c268-485e-854e-0398e6b2a323)

![Screenshot 2024-04-24 at 03 17 08](https://github.com/tvadhisti/module8-subscriber/assets/127074983/a630721f-a8a3-4165-a431-ee06f7bc6fea)

I ran the subscriber on three terminals and executed the publisher 4 or 5 times, and the queue showed only 5 unacknowledged messages. This shows that using more subscribers at the same time can really help in dealing with messages faster. Still, the messages are piling up a little, which means sometimes the publisher sends them faster than the subscribers can handle. If I use asynchronous processing in the subscribers, it could make things work better. This way, the subscribers wouldn't have to wait and could take messages as they come. Making this change would likely stop messages from getting backed up. It would keep the flow of messages smooth, even when the publisher is sending a lot.

