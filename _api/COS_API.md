---
layout: page
title:  "S3 Features Supported by IBM COS API"
featured: true
weight: 1
tags: [getting started, api, S3]
author: Mao Jia

dateAdded: June 29th, 2016
---

## Table of Contents
* [Overview](#overview)
* [Prerequisites](#prerequisite)
* [Common Headers and Error Responses](#headers-and-error-response)
* [Access Control Lists](#access-control-list)
* [Operations on the Service](#operations-on-service)
* [Operations on Objects](#operations-on-objects)

##  Overview
{: #overview}


	The Provisioning API Configuration allows an administrator to control the type of bucket provisioning requests available to users through the storage APIs. Provisioning user actions are disabled by default but can be set to Create Only or Create and Delete.
	
	If you want to use the provisioning API, [submit a Support ticket](../../userguides/Box_Panel/index.html#create-ticket) to ask the Support team to configure the feature for you.

## Common Headers and Error Responses
{: #headers-and-error-response} 

### Common Request Headers

|--------------------|------------|-------------------------------------|

For more information about the request headers, see [S3 API Common Request Headers](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTCommonRequestHeaders.html).


|----------------|-----------|------|
| Date           | Yes       |      |
| Server         | Yes       |      | 





{: #access-control-list}


| Email Address | Account username of user account (NOTE: Email address is an optional account attribute, so the account username is used in its place) | user1 |





|------------|------------|-----------|

{: #operations-on-service}




|-----------|-----------|-------|




|-----------|-----------|------|
| GET Bucket ACL | Yes |Requestor must be granted ``READ_ACL`` permission for bucket. |
| GET Bucket lifecycle | No | |
| GET Bucket Website | No |  |







## Operations on Objects
{: #operations-on-objects}



| Operation | Supported | Note |
| Complete Multipart Upload | Yes | |
 
For more information, see [S3 API Operations on Objects.](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectOps.html) and [Common Headers](#headers-and-error-response).

### GET Object


| Request Parameters | Yes |



|-----------|-----------|



| AWSAccessKeyId | Yes   | 
|-----------------|-----------|



**DELETE object support with COS:**

| Operation | Header | Supported |
|-----------|--------|-----------|
| Response Headers | x-amz-delete-marker | Yes |




### PUT Object


  <tr>
    <th>Operation</th>
    <th>Header</th>
    <th>Supported</th>
  </tr>
  <tr>
    <td rowspan="5">Request Headers</td>
    <td>Cache-Control</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>Expires</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>Policy</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>x-amz-server-side-encryption</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>x-amz-storage-class</td>
    <td>Ignored</td>
  </tr>
    <tr>
    <td rowspan="2">Response Headers</td>
    <td>x-amz-expiration</td>
    <td>No</td>
  </tr>
    <tr>
    <td>x-amz-server-side-encryption</td>
    <td>No</td>
  </tr>
</table>


### PUT Object (Copy)


  <tr>
    <th>Operation</th>
    <th>Header</th>
    <th>Supported</th>
  </tr>
  <tr>
    <td rowspan="5">Request Headers</td>
    <td>Expires</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>x-amz-acl</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>x-amz-server-side-encryption</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>x-amz-storage-class</td>
    <td>Ignored</td>
  </tr>
  <tr>
    <td>x-amz-copy-source</td>
    <td>Yes</td>
  </tr>
   <tr>
    <td rowspan="3">Response Headers</td>
    <td>x-amz-copy-source-version-id</td>
    <td>Yes</td>
  </tr>
   <tr>
    <td>x-amz-expiration</td>
    <td>No</td>
  </tr>
   <tr>
    <td>x-amz-server-side-encryption</td>
    <td>No</td>
  </tr>
 </table>
