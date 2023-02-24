# School Records based on Hyperledger Fabric
## Introduction
Apart from the security concerns, there are additional challenges related to secondary authentication and reliable storage of revision history, which can lead to increased costs. Additionally, the current system for accessing student transcripts can be time-consuming and inefficient for students.
To address these issues, implementing the Hyperledger Fabric blockchain can provide a solution. This permissioned blockchain technology allows for restricted access to authorized users, simplifies secondary authentication, and ensures data integrity through distributed storage of student records. By utilizing blockchain, students can access their documents more quickly and have greater control over their personal information. This solution also mitigates the risk of arbitrary data forgery and tampering.

This project will provide the following benefits:
1.	Secure and efficient way to manage requesting school transcript records
2.	Tamper-evident and transparent way to store and share student transcript between different education institutions
3.	Reduced administrative burden and improved data accuracy
4.	Enhanced data privacy and confidentiality
5.	Improved regulatory compliance


## Project Description
The proposed mechanism aims to strengthen the integrity of school transcripts based on blockchain. 
It can be largely divided into three types: write to record in the block network, query to check the recorded content, and request to request information on the block network.
<img width="452" alt="image" src="https://user-images.githubusercontent.com/114115158/221320583-713f023d-7ea2-4765-af6a-8d9b764523d5.png">
The proposed mechanism can execute chain code according to the transaction consensus process, and the transaction can be largely divided into a consensus process for reading information from student records and a consensus process for writing or creating student records. 


## Team
-	101445002 Yoodam Choi: As a business analyst, identify requirements and use-case and define workflows and processes to streamline operations. And collaborate with the development team to ensure the final product meets the needs and requirements. As a architect, develop a technical architecture that outlines the system’s components, their interaction and dependencies. Develop all the documents including solution design documentation. And ensure the final solution meets technical requirements and specifications.
-	100708985 Gordon Wells: As a blockchain developer, involves designing, developing, and implementing the smart contract, or chaincode, that define the business logic of the blockchain network. Deploy and configure the blockchain network infrastructure, which may involve configuring the nodes, setting up network channels, and ensuring the proper integration of various components of the network. 
-	101445536 Fetemeh Alipour Soweizi: As a full-stack developer, develop and maintain the user interface that interact with the network and the server-side logic that communicates with the network through SDKs. Integrate the blockchain network with other systems and services. 


## Requirements
Here is a high-level architecture for a Hyperledger Fabric solution for the education use case: 
1. Peers: 
Two types of peers can be defined in this solution: endorsing peers and ordering peers. Endorsing peers are responsible for endorsing transactions and executing chain code. For this solution, endorsing peers can be owned and maintained by each educational institution. Ordering peers are responsible for ordering transactions and creating blocks. They ensure that the transactions are executed in a proper sequence. In this solution, the ordering of peers can be managed by a trusted third party, such as a consortium of educational institutions or a government entity. 

2. CA (Certificates and Users): 
A Certificate Authority (CA) is used to issue and manage digital certificates that verify the identity of network participants. Each educational institution can have its own CA, which can issue certificates to students and staff. These certificates can be used to authenticate users and authorize their access to the network. Additionally, a trusted third party can also be responsible for issuing and managing certificates for the ordering peers. 

3. Orderer(s): 
In this solution, an orderer service can be set up, consisting of a number of ordering peers managed by a trusted third party. The orderer service ensures that all the transactions are processed in the correct order and creates blocks that are added to the blockchain. A solo orderer or a Kafka-based orderer can be used, depending on the network requirements.

4. Channel/s: 
Channels can be created to separate different types of transactions, such as student transcripts and faculty records. Each educational institution can have its own channel, with students endorsing peers from that institution and ordering peers from a trusted third party. Channels can be used to ensure that transactions are private and only visible to the participants in that channel.

5. MSPs:
Membership Service Providers (MSPs) are used to manage the identities of network participants and their access to the network. Each educational institution can have its own MSP, which is responsible for managing the identities of its students and staff. The trusted third party can also have an MSP, which can be responsible for managing the identities of ordering peers. This is just a high-level overview of the architecture. More details, such as the number of endorsing and ordering peers, the type of consensus algorithm to use, and the configuration of MSPs and CAs, will depend on the specific requirements of the use case.


## State Diagram
<img width="429" alt="image" src="https://user-images.githubusercontent.com/114115158/221320746-f9be9d20-92e8-469f-820d-672581cc8bf0.png">
In this diagram, the system starts in an Idle state, where the user can select to Request Transcript. Upon selection, the system transitions to the Transcript Requested state, where the Smart Contract validates the request and adds it to the blockchain.
Once the request is validated, the system transitions to the Request Validated state, where the Requesting School sends the transcript to be added to the blockchain. Once the transcript is added, the system transitions to the Transcript Received state.
The Requesting School then verifies the transcript, and the system transitions to the Transcript Verified state. From here, the Requesting School can share the transcript with a trusted network, and the system transitions to the Transcript Shared state.
Finally, the trusted network can access the transcript, and the system transitions to the Transcript Accessed state, where the Smart Contract logs the access. The system then returns to the Idle state, where it can start over with a new request.


## Sequence Diagram
![image](https://user-images.githubusercontent.com/114115158/221320821-bee99881-dea1-4112-b542-637f232a2cfa.jpeg)
In this sequence diagram, there are three main actors: the student, the institution, and the trusted network.
The sequence diagram shows the interactions between the actors in a typical use case scenario, which involves storing, retrieving, and sharing a transcript.

The sequence of events is as follows:
1.	The student requests a transcript from the institution.
2.	The institution retrieves the transcript from the blockchain ledger.
3.	The institution shares the transcript with the trusted network.
4.	The trusted network accesses the transcript from the blockchain ledger.
The sequence diagram provides a clear visualization of the interactions between the actors and the flow of data between them. It shows how the blockchain ledger is used to securely store and share transcripts and how the permissioned network model ensures that only authorized parties can access the data.

