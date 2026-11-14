# AWS S3 University Storage Management

A hands-on cloud storage project that simulates a university file management system using **Amazon Simple Storage Service (Amazon S3)**, **Python**, and **Boto3**.

The project organizes course materials, datasets, student submissions, and announcements in an S3 bucket, then demonstrates common object-storage operations through Python in Google Colab.

## Project Overview

Universities manage many types of digital files, including lecture slides, recordings, datasets, assignments, and announcements. This project demonstrates how these resources can be stored and managed in Amazon S3 using a structured object-key layout and Python automation.

## Technologies Used

- **Amazon S3** — Cloud object storage
- **Python** — Scripting and automation
- **Boto3** — AWS SDK for Python
- **Google Colab** — Notebook-based development environment

## Features Implemented

- Created an Amazon S3 bucket with a unique bucket name.
- Organized objects into logical prefixes for courses, datasets, submissions, and announcements.
- Uploaded and verified the project files in S3.
- Enabled S3 bucket versioning.
- Generated presigned URLs to provide temporary access to private objects.
- Listed and retrieved objects from the bucket.
- Updated objects and checked version history.
- Deleted selected objects and verified the deletion.
- Used Python and Boto3 to automate S3 operations.

## S3 Object Structure

The bucket uses the following logical structure:

```text
bucket-name/
├── courses/
│   ├── CS101/
│   │   └── weeks/
│   │       ├── week01/
│   │       │   ├── slides.pdf
│   │       │   └── lecture.mp4
│   │       └── week02/
│   │           └── slides.pdf
│   └── CS202/
│       └── weeks/
│           ├── week01/
│           │   └── slides.pdf
│           └── week02/
│               ├── slides.pdf
│               └── lecture.mp4
├── datasets/
│   ├── CS101/
│   │   └── marks.csv
│   └── CS202/
│       └── attendance.csv
├── submissions/
│   ├── CS101/
│   │   └── assignment1/
│   │       ├── 2023001/assignment.pdf
│   │       └── 2023002/assignment.pdf
│   └── CS202/
│       └── assignment1/
│           ├── 2023010/assignment.pdf
│           └── 2023011/assignment.pdf
└── announcements/
    ├── 2026-11-12.txt
    └── 2026-11-13.txt
```

> S3 is an object store. The folder-like structure shown above is represented by object keys and prefixes.

## Repository Structure

A suggested GitHub repository layout:

```text
AWS-S3-University-Storage-Management/
├── README.md
├── notebooks/
│   └── AWS_S3_University_Storage.ipynb
├── screenshots/
│   ├── 01_s3_bucket.png
│   ├── 02_uploaded_objects.png
│   ├── 03_versioning_bucket.png
│   └── 04_presigned_URL_demo.png
├── report/
│   └── AWS_S3_Project_Report.pdf
├── requirements.txt
└── .gitignore
```

Adjust the filenames to match the files you actually add to your repository. Do not commit private university files or real student submissions.

## Setup and Run

### 1. Requirements

- An AWS account
- An IAM identity with the required S3 permissions
- A Google account for Google Colab
- Python 3
- Boto3

Install Boto3 in the notebook:

```python
!pip install boto3
```

### 2. Configure Credentials Securely

In Google Colab, add these entries under **Secrets**:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION`

Enable notebook access for each secret. Do not paste credentials into notebook cells, upload them to GitHub, or share them in screenshots.

Example:

```python
import boto3
from google.colab import userdata

access_key = userdata.get("AWS_ACCESS_KEY_ID")
secret_key = userdata.get("AWS_SECRET_ACCESS_KEY")
region = userdata.get("AWS_DEFAULT_REGION")

s3 = boto3.client(
    "s3",
    aws_access_key_id=access_key,
    aws_secret_access_key=secret_key,
    region_name=region
)
```

### 3. Run the Notebook

Open the notebook in Google Colab, configure the required secrets, and run the cells in order. Set your own bucket name in the notebook; S3 bucket names must be globally unique.

## Security Considerations

- AWS credentials are not included in this repository.
- Keep S3 Block Public Access enabled unless there is a specific, reviewed reason to change it.
- Use IAM permissions limited to the actions required by the project.
- Presigned URLs grant temporary access to the specified object. Treat them as sensitive while they are valid.
- Use sample or synthetic data in public repositories and demonstrations.
- Review screenshots and notebook outputs before publishing to ensure they do not expose account IDs, credentials, private URLs, or personal information.

## Demo

A short demonstration video can show:

1. The S3 bucket and its organized object structure.
2. The uploaded course, dataset, submission, and announcement objects.
3. Bucket versioning enabled.
4. A presigned URL providing temporary access to an object.
5. Listing and reading objects with Boto3.
6. Updating an object and checking its versions.
7. Deleting an object and verifying the result.


## Learning Outcomes

By completing this project, I gained practical experience with:

- Cloud object storage concepts and Amazon S3.
- Managing buckets and objects through the AWS Console and Boto3.
- Organizing data with S3 object keys and prefixes.
- Bucket versioning and object version history.
- Presigned URLs for temporary object access.
- Automating create, read, update, and delete operations with Python.
- Basic cloud-storage security practices.

## Author

**M.ZUHAIB**

Computer Science Student | Learning Cloud Computing and AWS

---

*This project was developed as a hands-on university practical project to explore Amazon S3 and Python-based cloud storage management.*