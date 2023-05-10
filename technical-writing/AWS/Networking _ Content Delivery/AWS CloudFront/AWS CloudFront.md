## AWS CloudFront
Amazon CloudFront is a content delivery service/network(CDN) that works in conjunction with other Amazon Web Services (AWS) to provide developers with a simple way to distribute content to end users. 

This service is useful for companies with a need for higher response times and large file content that want to distribute these files to a sizeable number of users. Once content is put in an origin server, like an Amazon Simple Storage Service(S3) bucket or an Elastic Compute Cloud(EC2) instance, it’s pushed out to multiple CloudFront servers as content is requested.

CloudFront has features similar to dynamic site acceleration, a method used to improve online content delivery, but it can’t change the structure of content, like shrinking files or converting images into sprites.  CloudFront accelerates the delivery of dynamic content by moving it closer to the user to minimize internet hops involved in retrieving that content.

Amazon CloudFront is beneficial for someone developing a website that distributes a lot of content that needs to Scale-up. It can help reduce the costs and improve the performance of a website by providing high data transfer speeds, low latency and pay as you go pricing.

It retrieves data from Amazon S3 bucket and distributes it to multiple datacenter locations. It delivers the data through a network of data centers called edge locations. The nearest edge location is routed when the user requests for data, resulting in lowest latency, low network traffic, fast access to data, etc.

## How AWS CloudFront Delivers the Content?
AWS CloudFront delivers the content in the following steps.

Step 1- The user accesses a website and requests an object to download like an image file.

Step 2 − DNS routes your request to the nearest CloudFront edge location to serve the user request.

Step 3 − At edge location, CloudFront checks its cache for the requested files. If found, then returns it to the user otherwise does the following −

* First CloudFront compares the request with the specifications and forwards it to the applicable origin server for the corresponding file type.

* The origin servers send the files back to the CloudFront edge location.

* As soon as the first byte arrives from the origin, CloudFront starts forwarding it to the user and adds the files to the cache in the edge location for the next time when someone again requests for the same file. But this process is not quicker for the first user. However, when the second user accesses the same file, this file is already cached to the edge location, so it pulls the data from its edge location.

Step 4 − The object is now in an edge cache for 24 hours or for the provided duration in file headers. CloudFront does the following −

* CloudFront forwards the next request for the object to the user’s origin to check the edge location version is updated or not.

* If the edge location version is updated, then CloudFront delivers it to the user.

* If the edge location version is not updated, then origin sends the latest version to CloudFront. CloudFront delivers the object to the user and stores the latest version in the cache at that edge location.

## Key Terminology of CloudFront CDN

**Edge Location**: Edge location is the location where the content will be cached. It is a separate to an AWS Region or AWS availability zone.

**Origin**: It defines the origin of all the files that CDN will distribute. Origin can be either an S3 bucket, an EC2 instance or an Elastic Load Balancer.

**Distribution**: It is the name given to the CDN which consists of a collection of edge locations. When we create a new CDN in a network with aws means that we are creating a Distribution.

The distribution can be of two types:

* **Web Distribution**: It is typically used for websites.
* **RTMP**: It is used for Media Streaming.

## Features of CloudFront
**Fast** − The broad network of edge locations and CloudFront caches copies of content close to the end users that results in lowering latency, high data transfer rates and low network traffic. All these make CloudFront fast.

**Simple** − It is easy to use.

**Can be used with other AWS Services** − Amazon CloudFront is designed in such a way that it can be easily integrated with other AWS services, like Amazon S3, Amazon EC2.

**Cost-effective** − Using Amazon CloudFront, we pay only for the content that you deliver through the network, without any hidden charges and no up-front fees.

**Elastic** − Using Amazon CloudFront, we need not worry about maintenance. The service automatically responds if any action is needed, in case the demand increases or decreases.

**Reliable** − Amazon CloudFront is built on Amazon’s highly reliable infrastructure, i.e. its edge locations will automatically re-route the end users to the next nearest location, if required in some situations.

**Global** − Amazon CloudFront uses a global network of edge locations located in most of the regions.

### Procedures

1. Get a Domain name using any domain site of your choice
2. Goto Route 53 and register the domain name
3. Register the name servers in your domain name
4. Goto S3 and create a bucker using your domain name as the bucket name
5. Create your html file (index.html and
6. Use the bucket to host a static website
 error.html)
7. Upload the file to the bucket
8. Create Permission to your bucket
9. Check the site using the static end point

### Praticals

1. **Get a Domain name using any domain site of your choice:**

Goto Freenom and get a free domain

2. **Goto Route 53 and register the domain name:**

Goto **Route 53**, click on `Create hosted zone`

On the `Domain name`, add your domain name gotten from Freenom

Allow the `Type` to be Public

Click `Create hosted zone`.

3. **Register the name servers in your domain:**

Goto your Freenom and register the name servers shown in Route 53 to the domain name that you created

4. **Goto S3 and create a bucker using your domain name as the bucket name:**

Goto **S3**, click on Create bucket

On the **Bucket name**, and the domain name that you created

On **AWS Region**, select the region that you want your bucket to be hosted

Untick the **Block all public access**

Tick the **I acknowledge that the current settings might result in this bucket and the objects within becoming public**. That is below the bucket public access

Leave all other things on default settings

Scroll down and click on `Create bucket`

**N/B:** Make sure that public access is enabled i.e. publicly accessible and shown on the screen.

5. **Create your html file (index.html and error.html):**

Create a folder, create a file and name it **index.html**

Type `ht` and click on `html:5` and you can change the title

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Jason site</title>
    </head>
    <body>
        <h2>Welcome To My Site. For any inquiries, dial my number.</h2>
    </body>
    </html>

You can also create a **error.html** file using same process

6. **Use the bucket to host a static website:**

After the bucket has been created, click on the bucket name

Click on `Properties`

Scroll down to **Static website hosting**

Click on `Edit` that is at the right side

Tick `Enable`

On the **Index document**, type the name of the index file

On the **Error document**, type the name of the error file
Scroll down and click `Save changes`

7. **Upload the file to the bucket:**

Click on the bucket name

Click on `Upload`

Click on `Add files` or `Add folder`

Select the files/folders that you want and click  `Open`

It will take you back to the S3 bucket, scroll down and click `Upload`

The files will be uploaded


8. **Create Permission to your bucket:**

Click on the bucket name

Click on Permissions

On Bucket policy, click Edit

Click on Policy examples, this will take you to the documentation of S3 policy samples

Search for Granting read-only permission to an anonymous user

Copy the Policy sample, goto your S3 console and paste the policy on the policy editor

Delete the DOC-EXAMPLE-BUCKET on the policy and replce it with the bucket name

Eg. "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*" --> "arn:aws:s3:::mydomfree.tk/*"
Like:

    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "PublicReadGetObject",
                "Effect": "Allow",
                "Principal": "*",
                "Action": [
                    "s3:GetObject",
                    "s3:GetObjectVersion"
                ],
                "Resource": "arn:aws:s3:::mydomfree.tk/*"
            }
        ]
    }

9. **Check the site using the static end point:**

Click on Properties

Scroll down to Static website hosting

Copy the URL pasted below and paste on your browser to view you app or you can just click on it and see it running

10. CloudFront Configuration

Goto **CloudFront**, click on `Create a CloudFront distribution` to create a distribution

On the **Origin domain**, copy and paste the S3 bucket end point. Do not put the **http://** along with the URL

Scroll down, on the **Viewer**, tick **Redirect HTTP to HTTPS**

Scroll down to **Settings**, on **Alternate domain name (CNAME) - optional**, goto your freenom, copy and paste your domain name in the space

On the **Custom SSL certificate - optional**, click on **Request certificate**. It will take you to another page

Allow **Request a public certificate** to be ticked and click `Next`

On **Fully qualified domain name**, copy and paste your domain name there

Leave everything on default and click `Request`

Refresh the page to view your SSL cretificate

Click on the **Certificate ID** 

Scroll down, click **Create records** in Route 53 to create a record

It will take you to another page, Click **Create records**

And it will automatically create the record in your Route 53

You can check it by going back to your Route 53 and refresh the page and the record would appear

Check and refresh your SSL page to check if the certificate has been issued

If yes, goto your CloudFront and refresh the SSL certificate tab, click on the drop down and select the certificate that was issued

Scroll down to **Standard logging**, on **IPv6**, tick **Off** to switch off IPv6

Scroll down and click **Create distribution**.

11. **Create record for your domain name to direct traffics to CloudFront:**

Got o **Route 53**, click on your domain name

Click **Create record**

On **Record name**, leave it blank since your bucket does not have that www stuff

Leave **Record type** on **A – Routes traffic to an IPv4 address and some AWS resources**

Enable **Alias**

On **Route traffic to**,  click on the blank space and choose **Alias to CloudFront distribution**

Click on the space below and choose your **CloudFront Distribution domain name**

Click **Create records**.

12. Check if the site has been deployed with SSL certificate:

Goto your **CloudFront**, click on the cloudfront that you created

Copy the **Alternate domain names** and paste it on browser to see it working



