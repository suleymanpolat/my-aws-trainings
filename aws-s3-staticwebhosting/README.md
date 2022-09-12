# aws-s3-staticwebhosting

**Dynamic Hosting**

A dynamic website is a collection of dynamic web pages whose content changes in real time. Hosting such web pages to a web server is Dynamic Hosting. It accesses content from a database or Content Management System (CMS).

**Static Hosting**

Static web hosting supports fixed-content, HTML-based websites that display the same information to all visitors. When a user's web browser retrieves a static website from a static web hosting server, the entire page is already constructed in HTML files (along with possibly CSS and JavaScript).

**The purpose of this training** is to show an example how users can create a static web hosting by using AWS-Simple Storage Service (S3)

**Please follow the instructions step by step**

In this training, we will create a simple advocacy website by using S3 Amazon environment.

## Step 1 - Creat an S3 Bucket (Basic Operations)

* Sign in to AWS Console.

* Search for the S3 service on the bar and go to AWS S3.

* Click to the `create bucket`

* Fill the blanks in terms of details below:

```text
Bucket name                 : (write a unique bucket name)
Region                      : N.Virginia
Object Ownership            : ACLs disabled
Block all public access     : Unchecked
Versioning                  : ENABLED
Tagging                     : 0 Tags
Default encryption          : None
Object-level logging        : Disabled

```

* And click to the `create bucket`

Now you are ready to upload your static web site files into your bucket.

## Step 2 - Uploading website content files into your bucket

* Click to your **`BUCKET NAME`** and be sure that you see `properties` segment on the page (see the picture below)

<img width="1347" alt="Screen Shot 2022-09-05 at 20 07 28" src="https://user-images.githubusercontent.com/108346137/188493280-b00c5e26-85c0-49fc-8366-cde56d63e67b.png">

* Drag and drop `index.html`, `index.css` files and `img` folder into the console.

* And then click to `upload` to complete uploading files into your bucket.

## Step 3 - (Bucket Policy Settings) Give permission by using JSON to your bucket for your objects (content files) to be used together as website.

* * Click to your **`BUCKET NAME`** and be sure that you see `permisson` segment on the page (see the picture below)

![image](https://user-images.githubusercontent.com/108346137/188495624-20825818-8786-47f5-b702-415abd5f39b0.png)

* Click static web hosting and put check mark to `Use this bucket to host a website` and enter `index.html` as default file.

* Set the static website bucket policy as shown below (PERMISSIONS >> BUCKET POLICY) and change `bucket-name`  with your own bucket.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::don't forget to change with your bucket/*"
        }
    ]
}
```
* Save your changes.

## Step 4 - Configuring your bucket settings to host a static website

* See `properties` segment into your bucket (see the picture below)

![image](https://user-images.githubusercontent.com/108346137/188493804-446235c8-1103-4ba4-99bd-ee6f18488685.png)

* Scroll down and see the static website hosting.

![image](https://user-images.githubusercontent.com/108346137/188493987-8e842c30-313e-477b-94ae-c76e7d4d04fc.png)

* Please change your setting as below:

<img width="407" alt="Screen Shot 2022-09-05 at 20 23 11" src="https://user-images.githubusercontent.com/108346137/188494897-807f8733-dfc3-45af-bf34-0f7a2a965fe7.png">

* As soon as you save your changes you will get an static website hosting url. (see the picture below) 
* Please copy and paste this URL in a new tab of your browser.

<img width="1074" alt="Screen Shot 2022-09-05 at 20 36 19" src="https://user-images.githubusercontent.com/108346137/188496123-0da8860f-d27d-48f5-95c5-f90ad3523e71.png">

