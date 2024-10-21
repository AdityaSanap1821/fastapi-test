# FastAPI Application Deployment on Google Cloud Platform (GCP)

## 1. Introduction

This document outlines the process of deploying a FastAPI application on Google Cloud Platform (GCP).

## 2. Prerequisites

- Google Cloud account.
- Basic knowledge of FastAPI and Git.
- A virtual machine (VM) created in GCP.

## 3. Creating a Virtual Machine (VM)

To create a VM in GCP, follow these steps:

1. Go to the [Google Cloud Console](https://console.cloud.google.com).
2. Select your project or create a new one.
3. In the left sidebar, navigate to **Compute Engine > VM instances**.
4. Click on **Create Instance**.
5. Fill in the instance details:
   - **Name**: Give your instance a name.
   - **Region and Zone**: Choose a suitable region and zone.
   - **Machine type**: Select a machine type based on your needs (e.g., e2-micro for lightweight applications).
   - **Boot disk**: Choose an operating system (e.g., Ubuntu).
   - **Firewall**: Check the boxes for **Allow HTTP traffic** and **Allow HTTPS traffic**.
6. Click **Create** to launch your VM.

## 4. Setting Up the Environment

Connect to the VM via SSH and install the necessary packages using the following commands:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv git
```

## 5. Creating a Virtual Environment

After installing the necessary packages, create a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

## 6. Cloning the FastAPI Application

Clone the FastAPI application repository using the following command:

```bash
git clone https://github.com/AdityaSanap1821/fastapi-test.git
```

If the repository is private, use a Personal Access Token for authentication.

## 7. Setting Up the FastAPI Application

Navigate to the cloned repository:

```bash
cd fastapi-test
```

Install the necessary dependencies:

```bash
pip install fastapi uvicorn
```

## 8. Running the FastAPI Application

Run the FastAPI application using the following command:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

Access the application via the external IP of your VM:

```plaintext
http://<your-external-ip>:8000
```

## 9. Updating the FastAPI Application

To update your application after making changes to `main.py`

1. SSH into your VM.

2. Navigate to the cloned repository:
   ```bash
   cd fastapi-test
   ```
3. Pull the latest changes from your GitHub repository:
   ```bash
   git pull origin main
   ```
4. Restart the FastAPI application:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000
   ```

## 10 Troubleshooting Common Issues

If you encounter the error `ERR_SSL_PROTOCOL_ERROR`, ensure you are using HTTP and not HTTPS:

```plaintext
http://<your-external-ip>:8000
```

Check the firewall rules to ensure that port 8000 is allowed in GCP.

## 11 Conclusion

This document outlined the steps for deploying a FastAPI application on Google Cloud Platform. Deploying your application on GCP allows you to scale your service and take advantage of cloud resources.
