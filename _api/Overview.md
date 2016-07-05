---
layout: page
title:  "IBM Cloud Object Storage AWS CLI Overview"
featured: true
weight: 1
tags: [getting started, aws, cli, overview]
author: Mao Jia
dateAdded: June 8th, 2016
---



## Intended Purpose and Audience
The IBM Cloud Object Storage(COS) Application Programming Interface (API) enables application developers to use existing Amazon Simple Storage Service (S3) applications to access object buckets. When an object bucket is deployed, it is automatically made available through the Amazon S3 API.The IBM COS supports the most commonly used subset of Amazon S3 API operations. This document introduces the steps to use the Amazon Web Service (AWS) Command Line Interface (CLI) to manage your IBM COS service as a command line tool. 


## Using the AWS CLI S3 Tool

Using the AWS CLI in IBM COS requires a slight modification: setting the S3 endpoint. Other minor variations are outlined as follows.

For detailed information on SDK classes and functions, see the [AWS CLI S3 API Reference](http://docs.aws.amazon.com/cli/latest/reference/s3/index.html).
The examples in this document were generated using AWS CLI S3 1.7.36

Some sections refer to home directories. The user’s home directory vary per platform:| OS        |  Location           ||-----------|---------------------|| Linux     | /home/{username} ~/ || Windows 7 | %USERPROFILE%\      || Mac OS X  | /Users/{username}   |
This guide assumes a Unix/Linux development environment in the examples.### Using Secure HTTP
Take one of the following steps to use secure HTTP connections:* Configure the host to trust the Manager’s Certificate Authority (CA). Retrieve the Manager CA and follow the operating system’s instructions to install that CA.* Configure IBM COS with an external CA the host already trusts internally or externally.* Configure the SDK to ignore self-signed certificates at connect if the language supports it. This method is not recommended as it exposes your service to risk; the code will automatically trust any certificate.