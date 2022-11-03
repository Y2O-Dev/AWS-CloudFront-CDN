# Amazon CloudFront: Content Delivery Network (CDN)

Amazon CloudFront is a content delivery network operated by Amazon Web Services, which provide a globally-distributed network of proxy servers that cache content, such as web videos or other bulky media, more locally to consumers, thus improving access speed for downloading the content.

# Steps
* Creating S3 bucket 
* Uploading an image file
* Create a Custom_error directory in the bucket
* Configuration of the bucket policy 
* Configure CloudFront

## Creating S3 Bucket
* An S3 bucket name cloudfront-buckett-y2o was created, ensuring the obucket is publically available.

![s3_buckett](https://user-images.githubusercontent.com/114786664/199708608-48562e0c-bc8a-4e0e-8d31-9b4a62d1c628.png)

## Uploading an image file

* An image file smiley.jpg was uploaded to the bucket.

![s3_upload](https://user-images.githubusercontent.com/114786664/199709935-34026265-4687-4f4d-ae75-326b683760af.png)

![upload_success](https://user-images.githubusercontent.com/114786664/199709995-9da8a77a-3d1d-4f8b-814f-e1139d828620.png)

## Create a Custom_error directory in the bucket

* A custom error directory named Custom_error was created that will contain both error and block html file.

![error_folder](https://user-images.githubusercontent.com/114786664/199711306-24050cb0-c1b4-43c1-8a78-a8fd064b1d20.png)

![error_folder_content](https://user-images.githubusercontent.com/114786664/199711340-5cd73832-780b-4e32-8232-3717ff7899c0.png)

## Configuration of the Bucket Policy

* Appropriate bucket policy was  configured to allow access to the objects in the bucket. This is to ensure that the objects are accessible over the internet.

![bucket_policy](https://user-images.githubusercontent.com/114786664/199712494-8412410e-def8-46e5-b4f1-bbff895ae7f5.png)

## CloudFront Configuration

### Create a Cloudfront Distribution

* Create a CloudFront distribution and the choose the S3 to serve as the origin for the distribution

* It may take about 15min to deploy

* Copy the distribution domain name and test it in a web browser

![cloudfront_creation](https://user-images.githubusercontent.com/114786664/199730220-d417e8c5-c9e2-40fa-a9ee-9c0f2c5d3a81.png)

* The distribution url should display the image content of the bucket

![cloudfront_url](https://user-images.githubusercontent.com/114786664/199730373-1821f6ed-a326-4855-990b-b093aa607ea3.png)

### Custom error Response Configuration

* The custom error response is configured to return error page if wrong content is requested. It should be configured as follow:

![conf_error](https://user-images.githubusercontent.com/114786664/199734273-5b9b4e0e-7385-4e49-8c50-82a19596743c.png)

* The custom error response should be tested in a web browser by requesting for non-existence object in the bucket. This should return the below error page:

![error_page](https://user-images.githubusercontent.com/114786664/199735682-e10aef98-6197-4479-b91f-993485d820ef.png)

### Configuration of Geographical Restriction

* This to show how the CloudFront can be use to restrict access to content/s based on georaphical location
* A particular country is chosen to be added to the block list as shown in the diagram below.

![restriction](https://user-images.githubusercontent.com/114786664/199737533-a924e0ef-b26a-4040-867a-8a737e007767.png)

* After a georaphical location is added to the block list and we try to access it via the web browser, The below diagram is displayed because the specific error page to be displayed is yet to be configured

![restrictn_before_confg](https://user-images.githubusercontent.com/114786664/199738524-380ed302-fb1b-4a9d-ab38-18fb563f5d7d.png)

* To configure the block error page to be displayed, we'll create  another custom error response at the error page tab of the CloudFront console as shown below:

![conf_error_page](https://user-images.githubusercontent.com/114786664/199740465-5bb08a9e-cb19-4583-a2df-a0cea06e5843.png)

* We'll wait for the for the CloudFront distribution to complete deployment of the changes after which we'll then try to access the url from the restricted location:

* This should display the error page below

![block_error](https://user-images.githubusercontent.com/114786664/199741395-321d878b-d71a-4523-bf80-64ade886c0b3.png)

END
