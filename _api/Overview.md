---
layout: page
title:  "API Overview"
featured: true
weight: 1
tags: [getting started, API, overview]
author: Nick
dateAdded: August 18th, 2016
---


IBM Cloud Object Storage Dedicated IBM Managed (COS Dedicated IBM Managed) uses an implementation of the S3 API to interact with buckets and objects.

The following tables describe the complete set of supported operations when using the S3 API to access COS Dedicated IBM Managed.  For details on using the operations, including examples, see [the API reference page]({{ site.baseurl }}/gettingstarted/api/reference).

### Operations on the service

The only operation that is applied directly to account level is to get a list of buckets owned by that account. Accounts are limited to 100 buckets.

| Service operation | Note |
|:----|:---|
| `GET` Service | Used to retrieve of list of all buckets belonging to an account. |

### Operations on buckets

These operations create, destroy, get information about, and control behavior of buckets.

| Bucket operation | Note |
|:----|:---|
| `DELETE` Bucket | Deletes an empty bucket.   |
| `DELETE` Bucket CORS | Deletes any cross-origin resource sharing configuration set on a bucket. |
| `GET` Bucket | Lists objects contained in a bucket.  Limited to 1000 objects. |
| `GET` Bucket ACL |Retrieves the access control list for a bucket.|
| `GET` Bucket CORS |Retrieves any cross-origin resource sharing configuration set on a bucket.|
| `HEAD` Bucket | Retrieves a bucket's headers. |
| `GET` multipart uploads | Lists multipart uploads that have not completed or been canceled. |
| `PUT` Bucket | Buckets have naming restrictions. Accounts are limited to 100 buckets. |
| `PUT` Bucket ACL | Creates an access control list for a bucket. |
| `PUT` Bucket CORS | Creates a cross-origin resource sharing configuration for a bucket.|

### Operations on objects

These operations create, destroy, get information about, and control behavior of objects.

| Object operation | Note |
| :---------------| :------|
| `DELETE` Object | Deletes an object from a bucket.
| `DELETE` Multiple Objects  | Deletes multiple objects from a bucket.
| `GET` Object | Retrieves an object from a bucket.
| `GET` Object ACL | Retrieves an object's access control list.
| `HEAD` Object | Retrieves an object's headers.
| `OPTIONS` Object | Checks CORS configuration to see if a specific request can be sent.
| `POST` Object | Adds an object to a bucket using HTML forms.
| `PUT` Object | Adds an object to a bucket.
| `PUT` Object ACL | Creates an access control list for an object. 
| `PUT` Object (Copy) | Creates a copy of an object. |
| Initiate Multipart Upload | Creates an upload ID for a given set of parts to be uploaded.
| Upload Part | Uploads a part of an object associated with an upload ID.
| Upload Part (Copy) | Uploads a part of an existing object associated with an upload ID.
| Complete Multipart Upload | Assembles an object from parts associated with an upload ID.
| Abort Multipart Upload | Stops upload of parts associated with an upload ID.
| List Parts | Returns a list of parts associated with an upload ID
