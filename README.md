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
