# Static Website Deployment with AWS CodePipeline, S3, and CloudFront

This project sets up continuous integration and deployment for a static website using AWS CodePipeline, S3 for storage, CloudFront as the CDN, and GitHub as the source repository.



## Setup Instructions
 1.Create an S3 Bucket
- Go to the S3 console in AWS.
     Create a new bucket with a unique name (e.g., my-static-website-bucket).
     ![image-1](https://github.com/user-attachments/assets/3ba707fa-f566-43a1-b97d-5c6a7e71577d)
     Upload a html file in my-static-website-bucket.
     ![image2](https://github.com/user-attachments/assets/653ae35f-b709-4fbc-a59d-08033f4426ad)
     Enable "Static website hosting" in the properties of the bucket
     ![image3](https://github.com/user-attachments/assets/9cf069ce-d9dd-47e2-940f-c7f82fe6f95f)
     Set the appropriate bucket policy to allow public read access to the content (adjust if using CloudFront signed URLs).

### 2. *Set Up CloudFront*
   - In the CloudFront console, create a new CloudFront distribution.
   - Set the origin to your S3 bucket.
   - Configure the default cache behavior settings as needed.
   - Note the CloudFront distribution URL for later steps.

### 3. *Connect GitHub Repository to CodePipeline*
   - Go to the CodePipeline console.
   - Create a new pipeline and select GitHub as the source provider.
   - Authenticate with GitHub and select the repository and branch for the website.
   - Add an S3 bucket as the deployment destination.

### 4. *Configure CodeBuild (if needed)*
   - If your site requires a build step (e.g., npm build), configure CodeBuild in the pipeline.
   - Set up a buildspec.yml file in your repo to define build commands.

### 5. *Add S3 as the Deployment Provider*
   - In CodePipeline, add an S3 bucket as the deployment provider.
   - Point it to the previously created S3 bucket.

### 6. *Deploy and Verify*
   - Commit changes to the GitHub repository.
   - CodePipeline will automatically start and deploy the site to the S3 bucket.
   - Access the deployed website through the CloudFront distribution URL.

## Notes
- Ensure that appropriate permissions are set up for CodePipeline to access S3, GitHub, and CloudFront.
- CloudFront caching may delay changes; you can invalidate the cache if needed.

---

This guide should give users clear steps to replicate your setup! Adjust any specifics based on your project’s needs.
