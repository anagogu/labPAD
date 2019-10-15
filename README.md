# Message Broker
## Purpose of laboratory
Agent-based integration of messages that would allow asynchronous communication between the distributed components of a system.


> Defining the working protocol of the messaging agent

- The format (type) of messages to be transmitted. It is recommended to use XML format
- Number of unidirectional channels (variable / fixed, depending on the type of messages, etc.)
- The structure of the communication provided by the agent 
- Delivery policies for various cases defined by the agent's working logic

> Elaborate the abstract level of communication (network) necessary for the elements for receiving / sending messages by the transmitter to the receiver;
- The transport protocol is chosen depending on the objectives of the working protocol
- Concurrent processing of applications

> Elaboration of the elements that ensure the retention of the received messages 
- Transient method: messages will be stored in concurrent collections of specific data
of the selected language
- Persistent method: messages will be serialized / deserialized using methods
asynchronous or concurrent processing

> Elaborate the abstract level of message routing.

# Project arhitecture
The 3 subprojects included in the solution are the following:

- **sender** - the entity that sends out messages.
- **receiver** - the entity that subscribes to a certain type of messages and expects them
- **broker** - the middleware used to route the messages to subscribers

We chose to work with the **Maven** framework, having a later experience of working with this framework.
We added Apache Maven dependency in project POM
```
<dependency>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.8.1</version>
  <type>maven-plugin</type>
</dependency>
```
For data exchange format between browsers and web servers we used **Jackson**. It is a Java JSON API which provides several different ways to work with JSON. Jackson is one of the most popular Java JSON APIs out there. You can find Jackson [here!](https://github.com/FasterXML/jackson)


#####Jackson contains 2 different JSON parsers:

> The Jackson ObjectMapper which parses JSON into custom Java objects, or into a Jackson specific tree structure (tree model).
> The Jackson JsonParser which is Jackson's JSON pull parser, parsing JSON one token at a time.
> Jackson also contains two JSON generators:

> The Jackson ObjectMapper which can generate JSON from custom Java objects, or from a Jackson specific tree structure (tree model).
> The Jackson JsonGenerator which can generate JSON one token at a time.

Add Jackson dependency in POM:
```
<dependency>
  <groupId>com.fasterxml.jackson.core</groupId>
  <artifactId>jackson-core</artifactId>
  <version>2.9.6</version>
</dependency>
```
### Run application
The broker should be started first, it operates on port 4500 which is hardcoded in its source code thus it does not require any command line arguments.
```
try {
            Broker broker = new Broker(4500);
            broker.start();
        }
 ```
![Start Broker](https://github.com/anagogu/labPAD/blob/master/broker.png?raw=true)

After that it is possible to start a couple of instances of receivers. They should be told on which port to start, on what address and port is the broker located should the given receiver be subscribed to.
```
     Receiver receiver = new Receiver();
        receiver.startConnection("localhost", 4500);
```
Now that the broker and receivers are working, a sender can be deployed as well. 
All the sender should know is the address and port of the broker.
```
Sender sender = new Sender();
        sender.startConnection("localhost", 4500); 
```       
This already illustrates how decoupled is the sender from the receiver which is one of the main points of such an organisation of the system.

When started, the sender enters an infinite loop in which it asks the user to supply a message type and a message payload over and over again. The messages are then sent to the broker which consequently inspects the 'type' field of the message and dispatches it to the respective receivers.
```
 while (true) {
            Scanner scanner = new Scanner(System.in);
            String text = scanner.next();
            Message message = new Message(text, MessageOrder.SEND);
            sender.sendMessage(message);
        }
  ```
