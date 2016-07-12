---
layout: page
title:  "Installing and Configuring the AWS CLI"
featured: true
weight: 3
tags: [getting started, api, install, configure, AWS, CLI]
author: Mao Jia
dateAdded: June 8th, 2016
---
## Installing the AWS CLI
The AWS CLI can be [downloaded from Amazon](http://aws.amazon.com/cli/). Make sure that you download a version higher than 1.7.42.
For instructions on how to install the AWS CLI, see the [Amazon CLI documentation](http://docs.aws.amazon.com/cli/latest/userguide/installing.html).
## Configuring Authentication
The IBM COS API supports AWS Signature v2 and v4 Authentication.
The AWS Signature v4 signing specification describes how to add authentication information to S3 requests.Requests using AWS authentication must be signed using the requesting user’s Access Key ID and Secret Access Key, collectively known as Access Credentials.
The AWS Credentials file and AWS CLI Configuration file can contain one or more named set of Access Credentials, called named profiles. These files always have one set of Access Credentials which are identified as the ``[default]`` profile.
For information on how to obtian the Access Credentials, see [Obtian the Access Credentials](../../userguides/user_accounts/index.html#AccessCredentials).The order of precedence using for Access Credentials is as follows:
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
The AWS CLI sends all requests to ``s3.amazonaws.com`` by default.
To send requests to IBM COS, change the method to use a different hostname or IP address.Set the ``--endpoint-url`` option in the AWS CLI command with the following IP address:
**Placeholder for IP address and hostname**
**Note:** The AWS CLI interprets the http(s) portion of this endpoint and infer encrypted or plain text from the URL.

The COS API supports both Resource Path and Virtual Host Addressing.### Using Resource Path AddressingUse the ``--endpoint-url`` option of ``aws configure``:```
 aws --endpoint-url http://<IP_address> s3
``` ## Using Other OptionsAdditional options can be used in the main AWS CLI command. More information and examples can be found in the [Using High-Level s3 Commands with the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/using-s3-commands.html).