---
layout: post
title: Current State and ToDos for Klarrio Exercise
subtitle: Exercise 
gh-repo: frca-ctg/klarrio/ex1
gh-badge: [star, fork, follow]
tags: [test, mqtt, websockets, twisted]
---

## From Dev to Prod

Currently all work is done on a Virtualbox which represents the EC2 instance.
The following needs to be done in order to move over to EC2:
- Provision EC2 instance level
    - security groups and policies
    - instances
    - autoscaling
    - secrets vault for certificates and keys
- Provision EC2 application level
    - install python and libraries
    - git clone of the real-time service
    - startup of the service
- Provision S3 Static Website
    - AWS Cognito authentication setup
    - AWS s3 sync from github to s3 bucket

## Concept Validation: remaining ToDo

**Authentication**:
I tried Cognito as follows:
- configuration via AWS console (should be ansible or cloudformation)
- test case use with WebStack, Babel, React
ToDo: incorporate Cognito js files into Jekyll static website.

**Authorization**:
My website is on AWS account 'dev.casier', while the DynamoDB is on AWS account 'klarrio'.
I need to handle the authorization issues bdetween accounts.

**Security**:
- ToDo: Use of vault and ENV variables instead of hardcoded secrets.
- ToDo: HTTPS instead of HTTP.
- ToDo: WSS instead of WS
- ToDo: Policies to restrict EC2 websocket access (harden against DOS attacks) 

**Scalability**:
- Check system limits ifo number of websocket clients, mqtt traffic.

**High Availability**:
- Use MemCached/Redis to decouple EC2 instances running the RealTime service
- Use AutoScale to handle breakdown.

