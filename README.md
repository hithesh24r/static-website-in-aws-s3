# static-website-in-aws-s3
- Deployment of a Static Website over AWS S3 needs no other resources to be included and it is fairly easy to deploy
- Before doing this, a proper knowledge of AWS S3 and AWS IAM is neccesary to understand the concepts and components better
- Firstly, we need the files required for the website such as HTML, CSS, JavaScript, any attachments like images and videos
- After making the files and the codes ready, we can directly jump into AWS Management Console

## Step-1: Creating and logging into the AWS Management Console:
- Firstly, create an account on AWS (if you don't have one) and login to the AWS MAnagement console as a user
- Working on an IAM User account is better than working on a root account (If you want you can still skip creating the IAM user and go to the next step directly)
- If you don't have a IAM user already setup, then login with the root account and go to IAM console
- Then create a new user and select the required permissions (if you are creating a user for yourself then administrator permissions would be fine)
- But if you are creating the user to someone in your friends or your organization, then always follow "Least Priviledge Policy" i.e., giving the least amount of permissions which are required by the user
- Now, as the IAM user is created, logout of the root account and login with the IAM user credentials

## Step-2: Creating a S3 Bucket:
- Go to S3 Console in the Management Console
- Hit "Create Bucket" to initiate the starting of a new S3 bucket
- In the configuration of the bucket, select the region you want to work in (select a region nearest to the user)
- The give a name to the S3 Bucket (then S3 bucket name must be globally unique from all the accounts)
- Then leave the "Object Ownership" as it is as we dont need that section in this project
- Uncheck the "Block Public Access settings for this bucket" as we need this website to be accesable to the public
- "Bucket versioning" can be enabled if you think you may need the previous versions of the files in the future after making changes
- After that, create the bucket

## Step-3: Getting the Bucket ready for deploying static website:
- After creating the bucket, we have a option to upload files into the bucket
- Take all the files which are related to the static website and upload them to the S3 bucket
- Make sure that the path is not messed up while uploading the files
- After all the files are in the bucket, go to the properties and enable "Static Website Hosting" Option
- AWS S3 bucket will give you a URL which can be used to access the website
- But even though you enter the website in the search bar, the wensite won't show up
- S3 buckets needs something called a Bucket Policy, which  is a JSON file with all the permissions needed for the bucket to display the contents of the bucket

## Step-4: Creating and attaching the Bucket Policy to the created bucket:
- Go to the permissions of the bucket created for Static Website Hosting
- Go to the bucket policy tab and edit the bucket policy
- Add the contents of the file "**bucket-policy.json**" into the bucket policy in the console and then hit save
- In the above mentioned file, change the bucket name to the bucket name you gave to your bucket
- Now copy the link and paste it in the search bar of any browser, the contents of the static website are displayed over there
