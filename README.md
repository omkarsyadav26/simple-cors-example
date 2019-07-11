# simple-cors-example
Doc to read:- <https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html>

## What is CORS?
* Cross-Origin Request Sharing.
* By Default, Browser Prevent AJAX Request from another origin.
* CORS is a standard to relax the same origin policy.
* Selectively allow cross origin request while rejecting others.

## How to enable CORS?

* Add config.EnableCORS in WebAPIConfig.
* Add EnableCors attribute to the Controller class.
* Write CORSConfiguration file in S3 bucket.

----

### Example
In this example we are Enabling CORS on our static website hosted on S3.
* Create a bucket in s3 and make it public.
* Go inside the bucket and upload index.html and error.html in the bucket.
	* give them a public access and enable static website hosting.
* Create another bucket in s3 and make it public.
* Go inside the 2nd bucket and upload load.html file in it.
	* give it a public access and enable static website hosting.
	* write the CORSConfiguration in this bucket.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
<CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>GET</AllowedMethod>
    <MaxAgeSeconds>3000</MaxAgeSeconds>
    <AllowedHeader>Authorization</AllowedHeader>
</CORSRule>
</CORSConfiguration>
```
* update index.html file by changing the `load("2ND BUCKET LINK HERE")`.
