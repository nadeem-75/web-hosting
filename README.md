# Static Webpage Deployment with AWS CodePipeline, S3, and CloudFront

This project sets up continuous integration and deployment for a static website using AWS CodePipeline, S3 for storage, CloudFront as the CDN, and GitHub as the source repository.



## Setup Instructions
 1.Create an S3 Bucket
- Go to the S3 console in AWS.
    - Create a new bucket with a unique name (e.g., my-static-website-bucket).

     ![image-1](https://github.com/user-attachments/assets/3ba707fa-f566-43a1-b97d-5c6a7e71577d)

    - Upload a html file in my-static-website-bucket.
  
     ![image2](https://github.com/user-attachments/assets/653ae35f-b709-4fbc-a59d-08033f4426ad)

     -Enable "Static website hosting" in the properties of the bucket
  
     ![image3](https://github.com/user-attachments/assets/9cf069ce-d9dd-47e2-940f-c7f82fe6f95f)


 2. *Set Up CloudFront*
  - In the CloudFront console, create a new CloudFront distribution.
     
     ![WhatsApp Image 2024-11-12 at 7 17 12 PM](https://github.com/user-attachments/assets/bb1eb1cf-ee1e-4588-8911-67a2c4bc2b3d)


     - Set the origin to your S3 bucket.
       
    ![image4](https://github.com/user-attachments/assets/992daa3a-4fd0-43de-92ae-320a86a49e5f)

       
   - Configure the default cache behavior settings as needed.

      - Set the appropriate bucket policy to allow public read access to the content (adjust if using CloudFront signed URLs).

     ![image5](https://github.com/user-attachments/assets/8f0966e3-210b-4c95-a89f-5be53be2e131)
 
     
   - Check the CloudFront distribution URL.
     
     ![image7](https://github.com/user-attachments/assets/f92a21d0-3ca8-42f0-a5ee-abcad62365d1)


### 3. Connect GitHub Repository to CodePipeline
   - Go to the CodePipeline console.
   
     ![image8](https://github.com/user-attachments/assets/30c799ab-d38b-4a03-9df7-f7d8011ded37)

   - Create a new pipeline and select GitHub as the source provider.
   
     ![image9](https://github.com/user-attachments/assets/126ce83f-0a2f-4443-b326-dab2612c6397)


   - Authenticate with GitHub and select the repository and branch for the website.

     ![image13](https://github.com/user-attachments/assets/c9311881-0940-4b89-acac-72ccacea43b3)

   - Add an S3 bucket as the deployment destination.

     ![image14](https://github.com/user-attachments/assets/027004b6-aca6-455d-986d-e2f412b5ccf3)



   4. Add S3 as the Deployment Provider
   - In CodePipeline, add an S3 bucket as the deployment provider.
   - Point it to the previously created S3 bucket.

   5. Deploy and Verify
   - Commit changes to the GitHub repository.
   - CodePipeline will automatically start and deploy the site to the S3 bucket.
   - Access the deployed website through the CloudFront distribution URL.
     
   ![Screenshot 2024-11-10 215943](https://github.com/user-attachments/assets/4f1e7de3-765d-4974-835f-030d7f48882e)


- CloudFront caching may delay changes; you can invalidate the cache if needed.
