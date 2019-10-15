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


Jackson contains 2 different JSON parsers:

The Jackson ObjectMapper which parses JSON into custom Java objects, or into a Jackson specific tree structure (tree model).
The Jackson JsonParser which is Jackson's JSON pull parser, parsing JSON one token at a time.
Jackson also contains two JSON generators:

The Jackson ObjectMapper which can generate JSON from custom Java objects, or from a Jackson specific tree structure (tree model).
The Jackson JsonGenerator which can generate JSON one token at a time.
