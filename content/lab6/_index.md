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

In order have more control over the traces X-Ray records, it is possible to create custom segments in your applications
code (= instrumentation). An easy way to achieve this is by using the 
[xray sdk for python](https://docs.aws.amazon.com/xray-sdk-for-python/latest/reference/basic.html#) and the 
[Decorator for function auto-capture](https://docs.aws.amazon.com/xray-sdk-for-python/latest/reference/basic.html#decorator-for-function-auto-capture)
feature.

## Hints

- You can find an example implementation here: [Step 1](https://github.com/superluminar-io/sac-workshop/compare/lab5..lab6_a?expand=1)
- You can find an example implementation here: [Step 2](https://github.com/superluminar-io/sac-workshop/compare/lab6_a..lab6_b?expand=1)
