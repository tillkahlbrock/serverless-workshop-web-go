---
title: Lab 0 - Init
weight: 10
---

**In this Lab we will**:

- Setup the development environment
- Create our deployment pipeline
- Deploy a simple `hello-world` function
- Find logs and metrics for the function

**You completed this lab if you**:

- Successfully deployed the `hello-world` function
- Executed it once via the HTTP Endpoint (e.g using `curl`)
- Extended the function to generate some log output and found it in *Cloudwatch Logs*
- Took a look at the Dashboards for you function

## Setup

In order to setup the development environment in your AWS Account you have to log into the [AWS Console](https://console.aws.amazon.com/) via your
web browser. Use the user and credentials you created earlier.

Create the Cloudformation stack including the Cloud9 IDE and deployment pipeline using the following template:
```
https://serverless-workshop-eu-central-1-init.s3.eu-central-1.amazonaws.com/initial.template
```

Or simply click this button to launch the stack: [<img src="https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png">](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?templateURL=https://serverless-workshop-eu-central-1-init.s3.eu-central-1.amazonaws.com/initial.template)

## Cloudformation Stacks

If you check out the [Cloudformation console](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1) you will notice 2 stacks.

Try to figure out:

- Why are there two stacks, even if you just created one earlier?
- Which resources did the different stacks create?
- What output do they have?

## Deployment Pipeline

When the Cloudformation stacks got launched properly a [Code Pipeline](https://eu-central-1.console.aws.amazon.com/codesuite/codepipeline/home?region=eu-central-1) will be created.

The pipeline will have failed to complete the first run. But that's intended ;)

Try to figure out:

- How does the pipeline get triggered?
- What actions are performed during a pipeline run?
- How does the deployment of the `hello-world` function work?

## Hello World Function

To get a first impression of the involved AWS Components and the Web IDE we will deploy a simple `hello-world` function. The function has already been copied to your Cloud9 workspace.

Try to figure out:

- Why did the first pipeline run fail? 
- How to fix it?

## Hints

If you are stuck, here are some hints that might help you.

{{% expand "Hint 1" %}}
Take a look at the failed build step in Code Pipeline. There is `Details` link that leads to the console logs of the build.
{{% /expand %}}

{{% expand "Hint 2" %}}
Set a unique prefix at the top of the `Makefile` (e.g. `PREFIX := my-name-and-something`). Commit and push the changes. This should fix the pipeline :)
{{% /expand %}}
