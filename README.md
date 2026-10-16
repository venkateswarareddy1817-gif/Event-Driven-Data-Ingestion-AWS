# Event-Driven Data Ingestion System on AWS

## Project Overview
Implemented an event-driven data ingestion pipeline using AWS DynamoDB, DynamoDB Streams, AWS Lambda, Amazon SNS, and Amazon SQS. The system automatically processes order changes and sends notifications to a queue for downstream processing.

## Architecture
**DynamoDB → DynamoDB Streams → AWS Lambda → Amazon SNS → Amazon SQS**

## AWS Services Used
- **Amazon DynamoDB:** Stores order information.
- **DynamoDB Streams:** Captures changes to order records.
- **AWS Lambda:** Processes stream events and publishes notifications.
- **Amazon SNS:** Distributes order event notifications.
- **Amazon SQS:** Receives and stores notifications for asynchronous processing.
- **Amazon CloudWatch:** Supports Lambda log monitoring and troubleshooting.

## Workflow
1. Order records are inserted or updated in the DynamoDB `Orders` table.
2. DynamoDB Streams captures the changes.
3. Lambda processes the stream records.
4. Lambda publishes order event notifications to SNS.
5. SNS delivers notifications to the subscribed SQS queue.
6. Messages are verified in SQS to validate the pipeline.

## Testing
Tested the pipeline using four sample orders: `ORD1001`, `ORD1002`, `ORD1003`, and `ORD1004`. Verified that order event notifications reached the SQS queue.

## Project Structure
```text
Event_Driven_Data_Ingestion_AWS/
├── README.md
├── lambda_function.py
├── architecture.png
└── test_results/
    └── 01_dynamodb/
        └── dynamodb_table_items.png
```

## Outcome
Successfully demonstrated event-driven order processing and asynchronous message delivery using AWS managed services.

## Future Improvements
- Configure a dead-letter queue (DLQ) for failed messages.
- Add retry handling and monitoring alerts.
- Implement idempotency and secure IAM permissions for production use.
