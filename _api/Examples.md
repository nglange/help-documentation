---
layout: page
title:  "IBM Cloud Object Storage AWS CLI Examples"
featured: true
weight: 5
tags: [getting started, api, example]
author: Mao Jia
dateAdded: June 8th, 2016
---



**Note:** These examples are used to assist you in programming your own solutions and not be copied and pasted directly into your applications. ## Create a Bucket
Create a Bucket with the Make Bucket (mb) operation. 

```aws --endpoint-url=https://dsnet.example.com/ s3 mb s3://sample```
## Delete a BucketDelete a Bucket with the Remove Bucket (rb) operation. The following examples assume that Bucket ``sample`` already exists and is empty. 
``` 
aws --endpoint-url=https://dsnet.example.com/ s3 rb s3://sample```
To remove a non-empty bucket, you need to include the ``--force`` option to delete a Bucket and all Objects.```aws --endpoint-url=https://dsnet.example.com/ s3 rb s3://sample --force```The Remove Bucket (rb) operation with the ``--force`` parameter removes a Bucket and all of its Objects.
## Copy File/Object
The Copy (cp) operation copies a local file or Object to another location. The following examples assume that the ``sample`` and ``sample2`` Buckets already exist.

Copy (upload) a local file to the Bucket.
```aws --endpoint-url=https://dsnet.example.com/ s3 cp someFile.txt s3://sample```
Copy an Object within the same Bucket.```aws --endpoint-url=https://dsnet.example.com/ s3 cp s3://sample/someFile.txt s3://sample/someFileBackup.txt
```

Copy an Object between two Buckets.

```aws --endpoint-url=https://dsnet.example.com/ s3 cp s3://sample/someFile.txt s3://sample2/someFile.txt```
Copy a series of Buckets and Objects recursively.
```aws --endpoint-url=https://dsnet.example.com/ s3 cp path s3://sample/path --recursive```
Copy a series of Buckets and Objects recursively but exclude all files or Objects that matches the specified pattern.
```aws --endpoint-url=https://dsnet.example.com/ s3 cp path s3://sample/path --recursive --exclude "*.txt"```
## Download Object to a FileDownload an Object with the Copy (cp) and Move (mv) operations. The following examples assume that Bucket ``sample`` already exists.

Copy an Object to a File. 
```aws --endpoint-url=https://dsnet.example.com/ s3 cp s3://sample/myFile.txt retrieve.txt```
Move an Object to a File. 
```aws --endpoint-url=https://dsnet.example.com/ s3 mv s3://sample/myFile.txt retrieve.txt```**Note:** Both the ``cp`` and ``mv`` commands in the examples above download the Object to a local file. However, when using the ``cp`` command, the original Object remains in COS Dedicated IBM Managed while a copy is downloaded to local. When using the ``mv`` command, the Object is moved from COS Dedicated IBM Managed to local.  ## Move File
Move a local file or Object to another location with the Move (mv) operation. The following examples assume that the ``sample`` and ``sample2`` Buckets already exist.Move (upload) a local File to the Bucket.
```aws --endpoint-url=https://dsnet.example.com/ s3 mv someFile.txt s3://sample```
Move an Object within the same Bucket.
```aws --endpoint-url=https://dsnet.example.com/ s3 mv s3://sample/someFile.txt s3://sample/someFileBackup.txt
```Move an Object between two Buckets.
```aws --endpoint-url=https://dsnet.example.com/ s3 mv s3://sample/someFile.txt s3://sample2/someFile.txt
```## Delete ObjectDelete an Object with the Remove (rm) operation. 

Delete a single Object.

```aws --endpoint-url=https://dsnet.example.com/ s3 rm s3://sample/example.txt```
Recursively delete all Objects in a specified Bucket.
```aws --endpoint-url=https://dsnet.example.com/ s3 rm s3://sample/example.txt --recursive```
Recursive delete with all Objects in a specified Bucket while excluding some Objects.
```aws --endpoint-url=https://dsnet.example.com/ s3 rm s3://sample/example.txt --recursive --exclude "*.jpg"```
## List ObjectsList Objects and common prefixes under a prefix or all Buckets with the List (ls) operation. 

List all Buckets.

```aws --endpoint-url=https://dsnet.example.com/ s3 ls```
List all Objects under a specific Bucket.
```￼aws --endpoint-url=https://dsnet.example.com/ s3 ls s3://sample
```List all Objects under a specific Bucket with ``--page-size`` parameter.
```aws --endpoint-url=https://dsnet.example.com/ s3 ls s3://sample --page-size=2```
The ``--page-size`` parameter can limit the number of results in each response to a list operation. The default and maximum allowed value is 1000. Using a smaller value might help if an operation times out.