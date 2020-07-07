---
template: post
title: How to develop your microservice on AWS Lambda ?
slug: awslambda
draft: false
date: 2020-07-03T03:51:46.053Z
description: AWS Lambda for developing your microservices
category: 'System Design '
tags:
  - System Design
---
What are Microservices?

Microservices are an architectural and organizational approach to software development where software is composed of small independent services that communicate over well-defined APIs. These services are owned by small, self-contained teams.

Microservices architectures make applications easier to scale and faster to develop, enabling innovation and accelerating time-to-market for new features.

So we will look at how we can create it in AWS.

- AWS lambda provides simple way of running your code without the need to worry about the servers. The can be a quite helpful and cost-effective solution for your needs.

- Next step once your code is all settled in AWS is exposing it through API gateway. 

- With Amazon API Gateway you can map access to a specific resource (URL) with the HTTP method to the invocation of a Lambda function.
