# SQS - Create a Queue
Amazon SQS is a service that hosts the queue of messages (requests and responses) from the decoupled application components. 

![workflow](workflow.png?raw=true "workflow")

## A. Queues Dashboard
From the AWS management console, select SQS (Simple Queue Service).  
Start the Create queue wizard from there

## B. Create a Queue
A queue can be created quickly in three steps:  
1. General details - Provide a case-sensitive name, and choose the type of queue - Standard or FIFO, you want to create. A standard queue supports an unlimited number of transactions per second (TPS) for each API action (SendMessage, ReceiveMessage, or DeleteMessage). Whereas, FIFO queues support up to 3000 messages per second while strictly preserving the message order.  

![details](details.png?raw=true "details")

2. Configuration details - You can set the following items:  
Visibility timeout - The time-duration (0 seconds - 12 hours) after which a consumer message can become visible to the other consumers. Generally, the consumer must process and delete a message from the queue.  

Message retention period - The duration (1 minute - 14 days) for which the queue retains a message that does not get deleted. Amazon SQS will automatically delete messages that have been in a queue for more than the specified period.  

Delivery delay - The time (0 seconds - 15 minutes) to intentionally delay the delivery of each (new) message added to the queue. According to AWS:  
`If your consumers need additional time to process messages, you must delay each new message coming to the queue.`  

Maximum message size - It should be between 1 KB and 256 KB.  

![config](config.png?raw=true "config")

3. Access policy - You can define specifically who can send/receive messages to/from your queue. Choose the queue owner, or specified AWS accounts, IAM users, and roles as sender/receiver. The access policy can also be defined in JSON format.  

![policy](policy.png?raw=true "policy")

## C. Details of an Existing Queue
Select a queue from the Queues dashboard to view the basic details and configuration.

![existing](existing.png?raw=true "existing")

In the snapshot above, the URL https://sqs.us-east-1.amazonaws.com/572815612669/mysqs is an essential field to use in your application components. In addition, you can also view details about the Lambda triggers, and the access policy. You can even monitor various metrics, such as approximate age of message, the number of messages sent/received/delayed/deleted/empty receives, and size consumed by sent messages.  

## D. Send and receive messages
For the selected queue, you can either send/receive messages or configure Lambda function trigger. Let's see how to send and receive messages using a Standard queue.  
1. Send message  
![send](send.png?raw=true "send")

Receive messages  
A consumer cannot choose a specific message to receive. Instead, a consumer polls to receive up to 10 number of messages from the queue. The snapshot below shows a message received after polling. The default polling duration is set to 30 seconds.

Next, click on the message ID to view the message details, body, and metadata.
![receive](receive.png?raw=true "receive")

![receive2](receive2.png?raw=true "receive2")

## Summary
Step 1: Create a queue  
Step 2: Send a message  
Step 3: Receive and delete your message  
Step 4: Delete your queue  

