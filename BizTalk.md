# BizTalk
My journey with BizTalk, notes, class everything trying to include here

BizTalk Notes: 
**What is BizTalk? Who has developed? Why**

- BizTalk is a middleware product developed by Microsoft. It helps to connect various systems together to transmit the data. This BizTalk has been developed on. Net framework within Visual Studio, keeping in mind for usage at the enterprise level.
Middleware ->microsoft->built on .Net framework.

**Why has it developed?**

- Let's consider a scenario, i.e., I have files in Azure -> Azure Blob Storage, and it needs to be transmitted to SAP TM. How can we send it? There comes the BizTalk to transmit files among multiple systems like SAP, Azure, or any services. 
- Msg/Data will be received through Adapters, an endpoint to talk with systems, like collecting data from them and sending data to them.
- Ex: FTP, SFTP, FILE, Azure Blob Storage, SB Messaging
Azure -> SAP, FTP -> SAP, non-SAP -> SAP

<img width="1710" height="982" alt="image" src="https://github.com/user-attachments/assets/ea0495cc-551c-47da-a88f-062fa6cbed39" />

## BizTalk Archtiecture & Message Flow
BizTalk Server uses a publish-subscribe message flow, where messages are received by a receive port and its adapters, then processed by pipelines and optionally transformed by maps, before being published to the MessageBox database. From the MessageBox, subscribers, such as orchestrations or send ports, retrieve the messages that match their subscriptions to process and deliver them to their final destinations via send ports, pipelines, and adapters.  

<img width="1592" height="1194" alt="image" src="https://github.com/user-attachments/assets/3a7e2ace-0215-4c30-b9a2-411ae3178a53" />

**Artifacts—A Collection of items that helps to run BizTalk**

Here we have four fundamental building blocks/artifacts of BizTalk.

1.  Schemas—Structure of Msg
2. Maps—Defines the Msg from inbound to outbound
3. Pipelines—The process of messages, like conversion of messages to XML in the receive pipeline (disassembling and decoding from ANSI to UTF-8), and in the send pipeline, encrypting and assembling of messages takes place, like conversion of messages from XML to the required format and UTF-8 to ANSI.
4. Orchestration: Used to define business flow, and here is the place that maps get invoked.
Schemas: Are to define the structure of incoming messages

There are four types of schemas 

1. XML Schema/Document Schema
2. Flat File Schema
3. Envelope Schema
4. Property Schema
XML Schema: XML schema define the structure of messages in XML using XSD—XML Structure Definition language

Flatfile: Define the structure of the msg of the flat file based on delimiters, positional characters, or special characters. Ex: text, CSV.

Envelope Schema: Type of XML schemas used to combine multiple XML child elements into a single envelope schema

Property Schema: Property schemas are used to promote the fields or messages in the schemas. Promotion properties help with message routing across BizTalk.
