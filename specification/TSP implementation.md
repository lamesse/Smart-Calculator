# TAKO SERVER PROTOCOL V1.0 Specification



	Author              : REIS Rui, HEIG-VD
					  	  MESSERLI Antoine, HEIG-VD
	Last revision date  : 30.03.2014

	Revision history


## Table of Contents

1. [Introduction](#Introduction)
2. [Terminology](#Terminology)
3. [Protocol Overview](#ProtocolOverview)
	1. [System Architecture](#SystemArchitecture)
	2. [System Components](#SystemComponents)
		1. [Tako Main Server](#TakoMainServer)
		2. [Compute Engine](#ComputeEngine)
4. [Protocol Details](#ProtocolDetails)

## 1. <a name="Introduction"></a>Introduction

>The Tako Server Protocol (TSP) is the first part of the Tako Cloud Service, a cloud-computing engine. The second part, namely, the Tako Compute Protocol is defined by J. Bischof and H. Haiken [rfc-tako.txt]. The TSP is a stateless protocol and relies on UDP/IP transmission.

>It aims to provide computational engines stored in the cloud. The user connects to a central server which sends the back the available computational engines to which the user can connect. Their implementation is not specified here as they can be coded in any way imaginable.

>This documents explains how to add a computational engine to the Tako Cloud Service as well as how to connect to one.

## 2. <a name="Terminology"></a>Terminology

**TAKO**: octopus

**COMPUTE/COMPUTATIONAL ENGINE**: remote server accepting computation requests


## 3. <a name="ProtocolOverview"></a>Protocol Overview

>The user connects first to the Tako Main Server. The server sends a list of available compute engines and has two choices from there.
>
>1. Connect to a compute engine (specification in Tako Compute Protocol)
>
>2. Add his own compute engine (as specified in section 4)


### 3.1. <a name="SystemArchitecture"></a>System Architecture

>These diagrams show the interaction between a user and the server.

<center><img width=700 src="/images/TakoConnection.png"></center>

>The user has then 2 options

<center><img width=520 src="/images/TakoConnection2.png"></center>

### 3.2. <a name="SystemComponents"></a>System Components


#### 3.2.1. <a name="TakoMainServer"></a>Tako Main Server

>The Tako Main Server receives two types of requests:
>
>1. A [CONNECT] request which is answered by the list of computational engines
>
>2. An [ADD] request in which the the user has to provide the IP of his own computational engine so the server can add it to the list of available engines 

#### 3.2.2. <a name="ComputeEngine"></a>Compute Engine

>A compute engine is a remote server whose IP is known by the Main Server. Its task is to provide the user a list of possible computations. The interaction between an user and a compute engine is specified in the Tako Compute Protocol.


## 4. <a name="ProtocolDetails"></a>Protocol Details

>In this section, you should provide **all the information that is required for the readers to do a detailed design and an implementation of the software components** that will use your protocol to interact with each other. The readers should find a clear description of the communication patterns, the syntax and semantics of messages and of other rules defined by the protocol.

### 4.1. Transport Protocols and Connections

>In this paragraph, you should explain which protocols are used to transport application-level messages. You should define the standard port(s) (in the same way that HTTP defines 80 as the standard TCP port). You should also explain how the components start to interact with each other. If a connection is established, then how is it established and what is the procedure that needs to be implemented?

### 4.2. State Management

>In this paragraph, you should explain whether your protocol is stageful or stateless. If it is stageful, then you should describe all the states in which an application session can be, what events can happen in each of these states and what are the possible transitions between the states and what happens during these transitions.

>Start by showing a state machine diagram, which will give an overview to the readers. Then provide a detailed description of each state.

<center><img width=320 src="images/04/stateMachineDiagram.png"></center>


#### 4.2.1. State NAME_OF_THE_STATE_1

> In this paragraph, you should describe one particular state that appears on the state machine diagram. You should explain what it means for the conversation to be in this state. You should also explain what events are expected to happen while the conversation is in this state and what messages can be accepted from the other component. You should describe what should happen when these events happen (transition to another state, emission of a message, etc).
> 
> Sometimes, you will specify timing constraints in this part of the document. For example, you could state that when the conversation enters a particular state, then a timer is started and emits a signal after a given time. This signal would be considered as a specific event, that might trigger a transition to another state and other side effects (closing of a connection, emission of a message, etc.).

### 4.3. Message Types, Syntax and Semantics

>In this section, you should describe in details what messages are exchanged by system components, how they are structured and encoded, when they should be sent and what should happen when they are received.

> It is a good idea to write one paragraph for each type of message. Very often, you will also want to document some decisions that are valid for all messages. For example, you could state that all messages are encoded in JSON or in XML. Or, if you are using a grammar in your specification, you could state what kind of grammar it is and document the high-level production rules. Also, many protocol define a common structure for several message types, often involving the separation between an envelope (with headers) and a payload. This structure and the role of the headers may then be specified in an additional section that would be added here.

#### 4.3.1. Message MESSAGE_TYPE_1

>In this paragraph, you should provide all the details for one particular type of messages. You will therefore have one such paragraph for every type defined in your protocol.

### 4.4. Miscellaneous Considerations

> Depending on the actual system and protocol, you will need to address additional issues and specify various elements. Typical topics that are covered in protocol specifications include reliability, caching, scalability, content negotiation, encoding formats and others. You will have to adapt this part of the template to describe what is relevant to your own situation. If you have many questions to answer, then you will most likely split this section into multiple sections.

### 4.5. Security Considerations

>In many protocol specifications, security aspects of the protocol are treated in a dedicated section. Sometimes, the authentication, authorization, confidentiality rules are specified in the main protocol specification. Very often, however, the main protocol specification defines a generic mechanism (e.g. it states that requests should contain an authentication header, without fully specifying what should be transmitted in the header). Other specification documents are then written to use this extension point and to specify one or more different ways to actually handle the authentication in a system implementation. The HTTP specification follows this approach, with authentication mechanisms specified in [RFC 2617](https://tools.ietf.org/html/rfc2617). 

## 5. Examples

>In this section, you should **give examples of interactions between the components** of the distributed system. In previous sections, you have specified detailed rules (messaging patterns, session states, message syntax and semantics, etc.). Developers will use these detailed specifications when they implement your protocol.

>But by providing examples in the document, **you will help them in two ways**. Firstly, it will be **easier for them to understand what your protocol does and how**. Analyzing at a concrete dialog between a client and a server is often easier than directly digging into a more abstract definition. Secondly, it will allow them to **confirm their understanding of the protocol specification**. After reading the different rules specified in the previous sections, they will have a way to check that they have understood them correctly.


## 6. References

>Very often, you will provide references to other protocol specifications and/or to other documents. This is something that you should do in a specific section of your document.
