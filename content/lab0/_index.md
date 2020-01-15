---
title: Lab 0 - Init
weight: 10
---

**In this Lab we will**:

- Setup the development environment
- Use [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-command-reference.html)
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

Now we have to do the following steps to setup our development environment:

### Create Cloud9 Environment
- Open the [Cloud9 web interface](https://eu-central-1.console.aws.amazon.com/cloud9/home?region=eu-central-1#)
- Create a new environment
- Give it a name
- Leave all other settings untouched

### Bootstrap
- Open the terminal window and type:

    ```git clone --single-branch --branch lab0 https://github.com/superluminar-io/serverless-workshop-go.git```
- `cd serverless-workshop-go`
- `./bootstrap.sh`


### Test
- `sam --version`
- `aws sts get-caller-identity`

### Create a samconfig.toml
- `sam deploy --guided`
  - Stack name: ...
  - Region: eu-central-1
  - Confirm changes before deploy: Y
  - Allow SAM CLI IAM role creation: Y
  - Save arguments to samconfig.toml: Y

## Cloudformation Stacks

If you check out the [Cloudformation console](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1) you will notice 2 stacks.

Try to figure out:

- Why are there two stacks?
- Which resources do the different stacks contain?
- What outputs do they have?
