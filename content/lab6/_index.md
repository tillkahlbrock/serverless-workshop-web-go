---
title: Lab 6 - Tracing w/ X-Ray
weight: 40
---

**In this Lab we will**:

- Enable AWS X-Ray for our functions using AWS SAM
- Learn how distributed tracing works with AWS X-Ray 
- Instrument our application code to gain even more insights

**You completed this lab if you**:

- Can differentiate traces in X-Ray by HTTP Method (POST, GET, ...)
- Can tell how long your function needed to start (cold vs. warm)
- Can tell how long your function needed to persist and fetch data from DynamoDB

## Tracing with AWS X-Ray

[AWS X-Ray](https://aws.amazon.com/xray/features/) allows us to do distributed tracing in a way that we can trace 
invocations of our functions through the different AWS services.

### Step 1 - Build-in tracing

AWS SAM allows us to easily configure the X-Ray tracing mode for our lambda functions 
(check the `Tracing` [property](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#awsserverlessfunction)
of your function) 

### Step 2 - Instrument your applications codes

In order have more control over the traces X-Ray records, it is possible to add X-Ray tracing to your
AWS clients with the [xray sdk for go](https://github.com/aws/aws-xray-sdk-go).
The Clients will then trace the calls the other AWS service like DynamoDB or SNS.

### Step 3 - Create some traces

In order to create traces in X-Ray you have to call your functions. You can do this by either using the UI 
or a HTTP client like cURL. If you do not use the Web UI we deployed in [Lab4](/lab4) be sure to either 
set a valid `Authorization` header or disable [the authorization](https://github.com/superluminar-io/serverless-workshop-go/blob/071a75c4cc81924bc7bcacb07749c19e0f11fe0c/template.yaml#L36-L37) 
for now.

After invoking your functions, head to the X-Ray Service in the [AWS Console](https://eu-central-1.console.aws.amazon.com/xray/home?region=eu-central-1#/service-map).
You can find different views on the tracing data you just created.
Alternatively there is a section in Cloudwatch called [ServiceLense](https://eu-central-1.console.aws.amazon.com/cloudwatch/home?region=eu-central-1#servicelens:map).
It gives you a different view on the same data paired with a tighter UI.


## Hints

- You can find an example implementation here: [Step 1](https://github.com/superluminar-io/serverless-workshop-go/compare/lab5..lab6_a?expand=1)
- You can find an example implementation here: [Step 2](https://github.com/superluminar-io/serverless-workshop-go/compare/lab6_a..lab6_b?expand=1)
