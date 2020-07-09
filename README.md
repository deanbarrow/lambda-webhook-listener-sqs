# Lambda Webhook Listener to SQS

A serverless lambda function to listen for webhooks and send them to a SQS queue to consume in your own time. HTTP headers will be added as SQS message attributes.

More info: [Scalable webhook listener with Lambda and SQS](https://www.viadog.com/lambda-webhook-listener-sqs)

## Getting Started

These instructions will help get your function deployed and ready to use.

### Prerequisites

- An AWS account
- NodeJS
- [Serverless Framework](https://www.serverless.com/framework/docs/)

### Install

Clone the repo.

```
git clone https://github.com/deanbarrow/lambda-webhook-listener-sqs.git
```

Edit `serverless.yml` to set your profile name and region.

Install dependencies.

```
npm i
```

Deploy.
```
sls deploy
```

The output will show your webhook URL, the SQS queue name can be found in the AWS console.

## Sending a test webhook

Send a test webhook then check the SQS console to confirm it was received.

```
curl -X POST \
  https://xxx.execute-api.region.amazonaws.com/v1/webhook \
  -H 'Content-Type: application/json' \
  -H 'x-topic: webhook/test' \
  -H 'x-custom-header: testing' \
  -d '{
  "id": 12345,
  "key": "value"
}'
```

## Uninstall
```
sls remove
```