import json
import boto3
from datetime import datetime

currentDateAndTime = datetime.now()
my_message = "The current date and time is: " + str(currentDateAndTime)

def lambda_handler(event, context):
    client = boto3.client('sqs')
    
    response = client.send_message(
        QueueUrl='https://sqs.us-east-1.amazonaws.com/159288999110/queue_created_by_lambda',
        MessageBody=my_message
    )

    return {
        'statusCode': 200,
        'body': json.dumps("Message sent to sqs queue")
    }Click "Test"
