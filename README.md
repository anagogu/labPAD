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
'''<dependency>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.8.1</version>
  <type>maven-plugin</type>
</dependency>'''
