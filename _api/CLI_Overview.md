---
layout: page
title:  "Using AWS CLI"
featured: true
weight: 3
tags: [getting started, aws, cli, overview]
author: Mao Jia
dateAdded: June 8th, 2016
---

## Table of Contents
* [Overview](#overview)
* [Installing the AWS CLI](#installing-cli)
* [Configuring Authentication](#configuring-authentication)
* [Configuring the Storage Endpoint](#configuring-storage-endpoint)
* [Using Other Options](#other-options)
* [Supported Command Line Options](#supported-command-line)

## Overview
{: #overview}



### Using the AWS CLI S3 API Tool
{: #using-cli}

Using the AWS CLI in COS Dedicated IBM Managed requires a slight modification: setting the S3 API endpoint. Other minor variations are outlined as follows.

For detailed information on SDK classes and functions, see the [AWS CLI S3 API Reference](http://docs.aws.amazon.com/cli/latest/reference/s3/index.html).


Some sections refer to home directories. The user’s home directory vary per platform:


{: #installing-cli}


{: #configuring-authentication}





* Setting Credentials in Environment Variables




|--------------|-----------------------------------------------------------------------------------------------|

| Variable              | Purpose         |
|-----------------------|-----------------|
| AWS_ACCESS_KEY_ID     | AWS access key. |
| AWS_SECRET_ACCESS_KEY | AWS secret key. Access and secret key variables override credentials stored in both credential and config files. |
| AWS_SECURITY_TOKEN    | Security token. A web service that enables you to request temporary, limited-privilege credentials for AWS Identity and Access Management (IAM) users or for users that you authenticate (federated users). |
| AWS_PROFILE           | Name of the profile to use. This can be the name of a profile stored in a credential or config file or ``default`` to use the default profile. |

*Table 2. AWS CLI Supported Variables*

* The AWS CLI reads the Named Profiles settings in the default ``~/.aws/config`` file.



For example, the command output of ``aws configure`` can be as follows:

```
$ aws configure
For more information on ``aws configure``, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html).

To support multiple identities, AWS Credential Files can have Named Profiles.

aws configure --profile pool2
```

[default]
```

[default]

 

```

$ aws --profile pool2 s3 ls
```

## Configuring the Storage Endpoint
{: #configuring-storage-endpoint}




The COS Dedicated IBM Managed API supports both Resource Path and Virtual Host Addressing.
 aws --endpoint-url http://<endpoint_URL> s3
``` 
{: #other-options}




| Command  | Description         | Supported   | Unsupported options  |
|----------|---------------------|-------------|----------------------|