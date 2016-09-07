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
The IBM Cloud Object Storage Dedicated IBM Managed (COS Dedicated IBM Managed) Application Programming Interface (API) enables application developers to use existing Amazon Simple Storage Service (S3) applications to access object buckets. When an object bucket is deployed, it is automatically made available through the Amazon S3 API.COS Dedicated IBM Managed supports the most commonly used subset of Amazon S3 API operations. This document introduces the steps to use the Amazon Web Service (AWS) Command Line Interface (CLI) to manage your COS Dedicated IBM Managed service as a command line tool. 


### Using the AWS CLI S3 Tool
{: #using-cli}

Using the AWS CLI in COS Dedicated IBM Managed requires a slight modification: setting the S3 endpoint. Other minor variations are outlined as follows.

For detailed information on SDK classes and functions, see the [AWS CLI S3 API Reference](http://docs.aws.amazon.com/cli/latest/reference/s3/index.html).
The examples in this document were generated using AWS CLI S3 1.7.36

Some sections refer to home directories. The user’s home directory vary per platform:| OS        |  Location           ||-----------|---------------------|| Linux     | /home/{username} ~/ || Windows 7 | %USERPROFILE%\      || Mac OS X  | /Users/{username}   |
This guide assumes a Unix/Linux development environment in the examples.#### Using Secure HTTP
Take one of the following steps to use secure HTTP connections:* Configure the host to trust the Manager’s Certificate Authority (CA). Retrieve the Manager CA and follow the operating system’s instructions to install that CA.* Configure COS Dedicated IBM Managed with an external CA that the host already trusts internally or externally.* Configure the SDK to ignore self-signed certificates at connect if the language supports it. This method is not recommended as it exposes your service to risk; the code will automatically trust any certificate.## Installing the AWS CLI
{: #installing-cli}The AWS CLI can be [downloaded from Amazon](http://aws.amazon.com/cli/). Make sure that you download a version higher than 1.7.42.
For instructions on how to install the AWS CLI, see the [Amazon CLI documentation](http://docs.aws.amazon.com/cli/latest/userguide/installing.html).
## Configuring Authentication
{: #configuring-authentication}
The COS Dedicated IBM Managed API supports AWS Signature v2 and v4 Authentication.
The AWS Signature v4 signing specification describes how to add authentication information to S3 requests.Requests using AWS authentication must be signed using the requesting user’s Access Key ID and Secret Access Key, collectively known as Access Credentials.
The AWS Credentials file and AWS CLI Configuration file can contain one or more named set of Access Credentials, called named profiles. These files always have one set of Access Credentials which are identified as the ``[default]`` profile.
For information on how to obtain the Access Credentials, see [Obtain the Access Credentials](../../userguides/user_accounts/index.html#AccessCredentials).The order of precedence using for Access Credentials is as follows:
* Passing Credentials as Command Line Options
* Setting Credentials in Environment Variables* Setting Credentials in the Shared Credentials File
### Passing Credentials as Command Line Options
Use the AWS CLI as follows:
* Uses the GNU-style of command line options: full words preceded by two hyphens.* Can use options to override default configuration settings for a single operation.* Cannot specify Credentials.* Takes a string argument with a space or equals sign (=) separating the argument from the option name.**Note:** Quotes around the argument are not required unless the argument string contains a space.
| Option       | Purpose                                                                                       |
|--------------|-----------------------------------------------------------------------------------------------|| --profile    | Name of a Named Profile to use or default to use the default profile                          || --output     | Output format: {json\|text\|table}                                                              ||--endpoint-url| The URL against which the command acts. This can be the address of a proxy or an endpoint URL.|*Table 1. Command Line Options for the AWS CLI*### Setting Credentials in Environment VariablesEnvironment variables override configuration and credential files. They can be useful for scripting or temporarily using a Named Profile.

| Variable              | Purpose         |
|-----------------------|-----------------|
| AWS_ACCESS_KEY_ID     | AWS access key. |
| AWS_SECRET_ACCESS_KEY | AWS secret key. Access and secret key variables override credentials stored in both credential and config files. |
| AWS_SECURITY_TOKEN    | Security token. A web service that enables you to request temporary, limited-privilege credentials for AWS Identity and Access Management (IAM) users or for users that you authenticate (federated users). |
| AWS_PROFILE           | Name of the profile to use. This can be the name of a profile stored in a credential or config file or ``default`` to use the default profile. |

*Table 2. AWS CLI Supported Variables*

* The AWS CLI reads the Named Profiles settings in the default ``~/.aws/config`` file.* Credentials are read from and written to the default credentials file (``~/.aws/credentials``).### Setting Credentials in the Shared Credentials File
#### Creating Credentials
Use ```aws configure``` command to create an Access Credentials file with the ```default``` profile.

For example, the command output of ``aws configure`` can be as follows:

```
$ aws configureAWS Access Key ID [None]: #AKIAIOSFODNN7EXAMPLE# AWS Secret Access Key [None]: #wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY# Default region name [None]: Default output format [None]: #json# ```* The Access Key will be stored in ``~/.aws/credentials``.* The Secret Key will be stored in ``~/.aws/credentials``.* The Region does not need to be set. The user can press the Return key to skip this. The Region will be stored in ``~/.aws/config``.* The Output Format will be stored in ``~/.aws/config``.    
For more information on ``aws configure``, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html).

To support multiple identities, AWS Credential Files can have Named Profiles.Use ```aws configure — profile {profileName}``` to create an Access Credentials file with a Named Profile. Additional Named Profiles are appended to the ``~/.aws/credentials``.
For example, the command output of `` aws configure --profile pool2`` can be as follows:```
aws configure --profile pool2AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY Default region name [None]: Default output format [None]: json 
```* The Access Key will be stored in ``~/.aws/credentials``.* The Secret Key will be stored in ``~/.aws/credentials``.* The Region does not need to be set. The user can press the Return key to skip this. The Region will be stored in ``~/.aws/config``.* The Output Format will be stored in ``~/.aws/config``.An example of the AWS Credentials File (``~/.aws/credentials``) is as follows:
```
[default]aws_access_key_id = AKIAIOSFODNN7EXAMPLEaws_secret_access_key = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY[profile pool2]aws_access_key_id = N67W90RKLCWOLPSKN8W8aws_secret_access_key = RlfTDyqPg0WnY/PWdxMEe/gjuG7QRckynofRMwwR
```* The pool2 profile offers another set of Access Credentials for an S3 connection.  An example of the AWS Configuration File (~/.aws/config) is as follows:
```
[default]output=json[profile pool2]output=text```
#### Using Default CredentialsThis section uses the command for listing Buckets as an example. You can use other AWS commands similarly. 
 To list buckets by using the default Credentials, use the following command:
```$ aws s3 ls   
```To list buckets by using the a profile named ``pool2``, use the following command:
```
$ aws --profile pool2 s3 ls
```

## Configuring the Storage Endpoint
{: #configuring-storage-endpoint}
The AWS CLI sends all requests to ``s3.amazonaws.com`` by default.
To send requests to COS Dedicated IBM Managed, change the method to use a different hostname or IP address.Set the ``--endpoint-url`` option in the AWS CLI command with the [endpoint URL provided in the Lock Box](../../userguides/user_accounts/index.html#AccessCredentials).
**Note:** The AWS CLI interprets the http(s) portion of this endpoint and infer encrypted or plain text from the URL.

The COS Dedicated IBM Managed API supports both Resource Path and Virtual Host Addressing.### Using Resource Path AddressingUse the ``--endpoint-url`` option of ``aws configure``:```
 aws --endpoint-url http://<endpoint_URL> s3
``` ## Using Other Options
{: #other-options}Additional options can be used in the main AWS CLI command. More information and examples can be found in the [Using High-Level s3 Commands with the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/using-s3-commands.html).
## Supported Command Line Options
{: #supported-command-line}
S3 operations the COS Dedicated IBM Managed API supports might not map directly to these AWS CLI commands. The supported AWS CLI command lines are as follows. The unsupported options are noted.

| Command  | Description         | Supported   | Unsupported options  |
|----------|---------------------|-------------|----------------------|| cp       | Copies a local file or S3 Object to another location locally or in S3. | Yes | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || ls       | List S3 Objects and common prefixes under a prefix or all S3 Buckets. | Yes | --output || mb       | Creates an S3 Bucket.  |  Yes |   || mv       | Moves a local file or S3 Object to another location locally or in S3. | Yes   | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || rb       | Deletes an S3 Bucket.  | Yes |  || sync     | Syncs directories and S3 prefixes. Recursively copies new and updated files from the source directory to the destination. Only creates folders in the destination if they contain one or more files. | Yes | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || website | Set the website configuration for a Bucket. |No| |