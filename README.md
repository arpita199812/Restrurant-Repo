Hello Everyone,
In this project, first, I push my local repo to Github then to integrate with Github Action by making github workflows file and deploy our code to s3 by maiking yaml file.
To make the github workflows-
       - Go to Add new file in the same repo which you have to deploy
       - then create file by write this- **.github/workflows/DeployTos3.yml**
       - after that here, I simply use Github Action for pipelien and deployment 
       - then, I write the yaml script to deploy, you can see my script in my repo.
In AWS Cloud -
      - **IAM Service**
      - First, Go to IAM service
      - We need to **create IAM** for my s3 bucket 
      - Go to **Access Management** - click on **Users** - click on **create user** button
      - Specify user details- give **user name** - 'example'(name) - next
      - **Set permissions** - in Permissions options - **Choose Attach policy directly**
      - Permissions policies - **create policy** i.e., - AmazonS3FullAccess - click on next
      - Review and create -** click on create user**
      - Then you have to **create an access key and secret key id** for this IAM user
      - go to **Security Credentials section** - Access keys - Click on create access key - then Access key best practices & alternatives- choose - Other - next
      - Set description tag - optional - give and description, not mandatory - next
      - Then you will get Access key and Secret access key id you have to paste it on notepad because it will use in github action- workflow yaml script.
      - **S3 Service**
      - Second, I create a bucket with name i.e., 'my-first-bucket'
      - then, go in properties section and enable the static website hosting and write my 'index.html' file name
      - we also need to provide necessary permission to host the website, allow Block public access (bucket settings) and also need to create bucket policy.
To create bucket policy-
     - Click Edit section, and go to policy generator - then
     - Step 1: Select Policy Type - select the type of policy i.e., S3 Bucket Policy
     - Step 2: Add Statement(s)- Effect - Allow
                               - Principal - "arn:aws:iam::425033342492:user/github" - This is ARN (Amazon Resource Name) of IAM user who is authorized to access this s3 and create the bucket in S3.
                               - Amanzon Service - Automatically it show S3 because you already select policy type - S3 Bucket Policy
                               - Actions- in this actions we need to define which action and IAM user need to perform according to policy i.e., create, delete, update etc.
                               - Amazon Resource Name (ARN)- need to paste the already create s3 bucket ARN i.e., "Resource": "arn:aws:s3:::my-first-static-website1"
                               - Then, Click on Add Statement.
                               - After adding you get this line - You added the following statements. Click the button below to Generate a policy.
    - Step3: Generate Policy:
                              - Click on Generate Policy, you get the policy with version and Id.
                              - copy that policy and go to permission section - Bucket Policy - paste there the copied policy
                              
     - 


