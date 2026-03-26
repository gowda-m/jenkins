# Jenkins CI/CD Pipeline – Apache Static Website Deployment
---

## Project Overview

This project demonstrates a complete CI/CD pipeline implemented on a local machine using Jenkins to automate deployment of a static website to an Apache web server.

The pipeline pulls code from a GitHub repository and deploys the website to Apache’s document root directory, making it accessible via browser.

---

## Technologies Used

* Jenkins (CI/CD Automation)
* Apache HTTP Server
* Git & GitHub
* Linux (Local System)

---

## Step-by-Step Implementation

---

### Step 1: Install and Start Apache Server

Apache web server was installed and configured on the local machine.

```bash
sudo zypper install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

Verification:

* Open browser and access:

```
http://localhost
```

📸 **Screenshot – Apache Running**
![Apache](screenshots/08_apache_running.png)

---

### Step 2: Install and Setup Jenkins

Jenkins was installed and started on the local system.

```bash
sudo zypper install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Access Jenkins:

```
http://localhost:8080
```

Initial setup:

* Enter admin password
* Install suggested plugins

**Screenshot – Jenkins Dashboard**
![Jenkins Dashboard](screenshots/01_jenkins_dashboard.png)

---

### Step 3: Configure SSH Access (Local Deployment)

SSH was configured to allow Jenkins to deploy files to the Apache directory.

Generate SSH key:

```bash
ssh-keygen -t rsa
```

Copy key to local system:

```bash
ssh-copy-id root@localhost
```

Test SSH:

```bash
ssh root@localhost
```

This ensures passwordless authentication for deployment.

**Screenshot – SSH Setup**
![SSH Setup](screenshots/03_git_config.png)

---

### Step 4: Create Jenkins Pipeline Job

* Open Jenkins Dashboard
* Click **New Item**
* Enter job name
* Select **Pipeline**
* Click OK

📸 **Screenshot – Job Creation**
![Job Creation](screenshots/02_new_job.png)

---

### Step 5: Configure GitHub Repository

* Connected Jenkins with GitHub repository
* Added repository URL in pipeline configuration
* Configured branch (main/master)

**Screenshot – Git Configuration**
![Git Config](screenshots/03_git_config.png)

---

### Step 6: Configure Pipeline

* Pipeline configured to use Jenkinsfile from repository
* No inline script used (Jenkinsfile maintained in GitHub)

**Screenshot – Pipeline Configuration**
![Pipeline Config](screenshots/04_pipeline_config.png)

---

### Step 7: Trigger Build

* Build triggered manually using **Build Now**
* Jenkins started executing pipeline stages

**Screenshot – Build Trigger**
![Build](screenshots/05_build_trigger.png)

---

### Step 8: Verify Console Output

* Console output checked for successful execution
* Verified code checkout and deployment steps

**Screenshot – Console Output**
![Console](screenshots/06_console_output.png)

---

### Step 9: Check Pipeline Stage View

* All stages completed successfully
* No failures observed

**Screenshot – Pipeline View**
![Pipeline View](screenshots/07_pipeline_view.png)

---

### Step 10: Verify Website Deployment

The website file (`index.html`) was deployed to:

```
/var/www/html/
```

Accessed in browser:

```
http://localhost
```

**Screenshot – Website Live**
![Website](screenshots/09_website_live.png)

---

## CI/CD Workflow

1. Code pushed to GitHub repository
2. Jenkins pipeline triggered
3. Jenkins pulls latest code
4. Deployment executed via pipeline
5. Files copied to Apache directory
6. Website becomes live in browser

---


## Final Result

* Successfully implemented CI/CD pipeline locally
* Automated deployment using Jenkins
* Static website deployed and verified on Apache

---

## Notes

* This setup is for local practice and testing
* Deployment handled using Jenkins pipeline
* SSH configured for seamless automation

