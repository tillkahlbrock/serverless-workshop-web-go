---
title: Lab 1 - URL Shortener
weight: 15
---

**In this Lab we will**:

- Create a first basic version of our url shortener
- Learn how to store data in AWS DynamoDB using the AWS Python SDK (boto3)
- See some more advanced features of AWS SAM

**You completed this lab if you**:

- Shortened at least one URL
- Typed the shortened URL into your browser and got redirected properly

## Implement a URL shortener using [DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html) for storage with two functions.

- Implement one function to create a shortened URL via HTTP POST
- Implement one function to retrieve the full URL via HTTP GET issuing a `302 Found` redirect

Below you find an example interaction with your service:

```
$ curl -v -XPOST -d '{"url": "https://superluminar.io"}' https://$ENDPOINT

> POST /short-url HTTP/1.1
< HTTP/1.1 Created 201
Created short url: https://$ENDPOINT/${short-id}

$ curl -v https://$ENDPOINT/${short-id}

> GET /${short-url} HTTP/1.1
< HTTP/1.1 302 Found
< Location: https://superluminar.io
```

{{<mermaid>}}
sequenceDiagram
    participant Browser
    participant APIGateway
    participant Lambda
    participant DynamoDB
    Browser->>APIGateway: POST /short-url
    APIGateway->>Lambda: Invoke
    Lambda->>DynamoDB: PutItem
    DynamoDB-->>Lambda: OK
    Lambda-->>APIGateway: {"url": "foo"}
    APIGateway-->>Browser: HTTP 201 Created {"url": "foo"}
{{< /mermaid >}}

## Hints

- Use boto3 to [use the DynamoDB API](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
- Create a DynamoDB table using AWS SAM (e.g [AWS::Serverless::SimpleTable](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template.html#serverless-sam-template-simpletable))
- Give your Lambda functions permissions to access the DynamoDB table with [SAM Policy Templates](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-policy-templates.html)
- Inject the DynamoDB table via [environment variables](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#environment-object) into your [Lambda function](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#properties)
- Use path parameters with [API Gateway](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#api) and Lambda
- Generate a short unique ID for the URL ([e.g.](https://stackoverflow.com/a/2510733))
- Try it!

You can find an example implementation here: https://github.com/superluminar-io/sac-workshop/compare/lab0..lab1?expand=1
