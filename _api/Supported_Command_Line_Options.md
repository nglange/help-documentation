---
layout: page
title:  "Supported Command Line Options"
featured: true
weight: 4
tags: [getting started, api, aws, cli]
author: Mao Jia
dateAdded: June 8th, 2016
---



S3 operations the COS API supports might not map directly to these AWS CLI commands. The supported AWS CLI command lines are as follows. The unsupported options are noted.

| Command  | Description         | Supported   | Unsupported options  |
|----------|---------------------|-------------|----------------------|| cp       | Copies a local file or S3 Object to another location locally or in S3. | Yes | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || ls       | List S3 Objects and common prefixes under a prefix or all S3 Buckets. | Yes | --output || mb       | Creates an S3 Bucket.  |  Yes |   || mv       | Moves a local file or S3 Object to another location locally or in S3. | Yes   | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || rb       | Deletes an S3 Bucket.  | Yes |  || sync     | Syncs directories and S3 prefixes. Recursively copies new and updated files from the source directory to the destination. Only creates folders in the destinationif they contain one or more files. | Yes | --acl Bucket-owner-read option --acl Bucket-owner-full-control --website -redirect --source-region --grants full={emailAddress\|userName} || website | Set the website configuration for a Bucket. |No| |