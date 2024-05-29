# Static-Site-Cloudfront


### 1. Create an S3 Bucket

1. Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to the S3 service and click on "Create bucket".
3. Name your bucket (e.g., `my-static-site`) and select the appropriate region.
4. Uncheck "Block all public access" to make the bucket public.
5. Enable static website hosting in the bucket properties and specify `index.html` as the index document.

### 2. Upload Website Files

1. Upload your static website files (HTML, CSS, JS) to the S3 bucket.
2. Set the permissions to make the files publicly readable.

### 3. Set Bucket Policy

Add the following bucket policy to allow public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}


Replace 'your-bucket-name' with the name of your bucket and save the policy.

Step 4: Create a CloudFront Distribution
Navigate to the CloudFront console and click "Create Distribution."
Choose "Web" for the delivery method.
Set your S3 bucket as the origin. Enter the bucket's endpoint URL (found in the S3 bucket properties under "Static website hosting").
Configure settings:
For "Origin Access Identity," select "Create a New Identity" to ensure only CloudFront can access your S3 bucket.
Add the index document name under "Default Root Object."

Step 5: Test Your Setup
Access your website using the CloudFront distribution domain.

Goodluck!
