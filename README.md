# TASK 8: Run a Simple Java Maven Build Job in Jenkins
## Objective:

Learn how to use Jenkins to build a simple Java application using Maven — your first step into CI/CD.
### 🛠️ Tools Required (All Free):
* Jenkins (installed locally or via Docker)
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20173533.png?raw=true)

* Java JDK 8 or 11
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20173605.png?raw=true)

* Maven
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20173634.png?raw=true)

* Git (optional — can run from local folder)
### 📂 Deliverables:
* A basic Java HelloWorld app (with pom.xml)
* Jenkins Freestyle job configured to build it
* Screenshot of successful build console output
### 📦 Sample Dataset/Repo:
* Repo name: hello-java-maven
* Contents:
  * pom.xml
  * src/main/java/HelloWorld.java


## Start Jenkins:
**Use Azure VM -> Install Jenkins -> add inbound Rule:8080 -> http://localhost:8080***

In Jenkins:
### Go to Manage Jenkins → Global Tool Configuration → Add Maven (e.g., Maven 3.8.6)
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172008.png?raw=true)

### Create a new Freestyle project
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20155609.png?raw=true)
![image_url]https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20171639.png?raw=true)

### In Build section, select: Invoke top-level Maven targets
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172149.png?raw=true)

### Set Goal: clean package
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172149.png?raw=true)

### Save & Build the job
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/screencapture-4-240-102-109-8080-job-hello-java-maven-configure-2026-02-24-17_31_29.png?raw=true)
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172349.png?raw=true)

### Check Console Output → You should see: BUILD SUCCESS
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/screencapture-4-240-102-109-8080-job-hello-java-maven-2-console-2026-02-24-17_30_42.png?raw=true)
