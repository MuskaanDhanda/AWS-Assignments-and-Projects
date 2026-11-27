# Module 6: S3 Bucket

> **Original Word document:** [Module 6-S3 Bucket.docx](Module%206-S3%20Bucket.docx)

## Contents

- [A. S3 Bucket Creation](#a-s3-bucket-creation)
- [B. Bucket Versioning](#b-bucket-versioning)
- [C. Website Hosting and Lifecycle Rule](#c-website-hosting-and-lifecycle-rule)

> **Problem statement (all S3 assignments):** You work for XYZ Corporation. Their application requires a storage service that can store files and publicly share them if required. Implement S3 for the same.

---

## A. S3 Bucket Creation

### Task 1: Create an S3 bucket for file storage

![Screenshot 01](images/01.png)

![Screenshot 02](images/02.png)

### Task 2: Upload 5 objects with different file extensions

![Screenshot 03](images/03.png)

---

## B. Bucket Versioning

![Screenshot 04](images/04.png)

### Task 1: Enable versioning for the bucket created in task A

![Screenshot 05](images/05.png)

![Screenshot 06](images/06.png)

Click **Save changes**.

![Screenshot 07](images/07.png)

### Task 2: Re-upload 2 files that were already uploaded to verify versioning works

![Screenshot 08](images/08.png)

![Screenshot 09](images/09.png)

---

## C. Website Hosting and Lifecycle Rule

### Task 1: Use the bucket to host a static website and upload index.html and error.html

![Screenshot 10](images/10.png)

![Screenshot 11](images/11.png)

![Screenshot 12](images/12.png)

![Screenshot 13](images/13.png)

![Screenshot 14](images/14.png)

![Screenshot 15](images/15.png)

![Screenshot 16](images/16.png)

![Screenshot 17](images/17.png)

![Screenshot 18](images/18.png)

![Screenshot 19](images/19.png)

![Screenshot 20](images/20.png)

### Task 2: Add a lifecycle rule for the bucket

![Screenshot 21](images/21.png)

**a. Transition from Standard to Standard-IA in 60 days**

![Screenshot 22](images/22.png)

![Screenshot 23](images/23.png)

**b. Expiration in 200 days**

![Screenshot 24](images/24.png)
