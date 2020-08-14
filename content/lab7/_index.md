---
title: Lab 7 - Alerting
weight: 45
---

**In this Lab we will**:

- Take a look at Cloudwatch Metrics 
- Create two alerts based on these metrics
- Trigger an alert and see what happens

**You completed this lab if you**:

- Created at least one [Cloudwatch Alarm](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-cw-alarm.html)
- Generated metrics in a way, that your alarms got triggered

**Why is this important**

When using serverless components from AWS you leave big part of the heavy lifting to Amazon. 
This gives you the advantage not having to worry about monitoring your servers anymore.

Despite that there are still things that could go wrong:

- You can deploy code that only errors under certain circumstances, not covered by you integration tests.
- You can hit the memory limit of you function.
- Your function can get throttled, because there are not enough 
[reserved concurrency](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html) left. 

## Alerting with Cloudwatch Alarms

With Cloudwatch Alarms it is fairly easy to create alerts alongside your function definition. These alerts utilize 
on Cloudwatch metrics. The metrics can be used in two different ways:

- You can just use the **bare metric** like `Invocations`.
- You can use **math expressions** like `Errors / Invocations` to alert based on error rate.
- (There are also [composite alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)), but we ignore them here.)

Steps to take in this lab:

- Take a look a [Cloudwatch metrics](https://eu-central-1.console.aws.amazon.com/cloudwatch/home?region=eu-central-1#metricsV2:graph=~()) 
or [the docs](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-metrics.html)
- Set yourself to a metric you want to use in your alarm
- Write some [cloudformation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-cw-alarm.html) to create the alarm
- Modify your function if needed (e.g. use `sleep` or let it error on certain inputs)
- Call your function to trigger an alarm

## Hints

- You can find an example implementation here: https://github.com/superluminar-io/serverless-workshop-go/compare/lab6_b..lab7_alarm?expand=1
