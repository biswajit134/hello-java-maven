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
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20171639.png?raw=true)

### In Build section, select: Invoke top-level Maven targets
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172149.png?raw=true)

### Set Goal: clean package
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172149.png?raw=true)

### Save & Build the job
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/screencapture-4-240-102-109-8080-job-hello-java-maven-configure-2026-02-24-17_31_29.png?raw=true)
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/Screenshot%202026-02-24%20172349.png?raw=true)

### Check Console Output → You should see: BUILD SUCCESS
![image_url](https://github.com/biswajit134/hello-java-maven/blob/main/SS/screencapture-4-240-102-109-8080-job-hello-java-maven-2-console-2026-02-24-17_30_42.png?raw=true)


## Interview Questions:


1. What is Jenkins?
Jenkins is an open-source automation server used to automate parts of the software development process. It is the most popular tool for Continuous Integration (CI) and Continuous Delivery (CD).

* Core Function: It allows developers to continuously integrate their code changes into a shared repository. Jenkins detects these changes, triggers a build, runs tests, and can deploy the application.

* Key Benefit: It catches errors early (fail fast) and standardizes the build process, reducing manual work and "it works on my machine" issues.

2. How do you create a Jenkins job?
To create a new job (often called a "Project" or "Item") in Jenkins, follow these general steps:

    1. Dashboard: From the Jenkins Dashboard, click on "New Item" in the top left corner.

    2. Name & Type: Enter a name for your job and select the type of project. The two most common are:

        * Freestyle project: A web-based GUI for configuring simple build steps.

        * Pipeline: Uses a Jenkinsfile (scripted or declarative) to define the entire build process as code.

    3. Configuration: Once created, you configure the job details:

        * Source Code Management: Connect to Git/GitHub/Bitbucket.

        * Build Triggers: Define when the job runs (e.g., "Poll SCM" or Webhooks).

        * Build Steps: Define what the job actually does (e.g., run a Maven script, execute a shell command).

    4. Save: Click "Save" or "Apply."

3. What is Maven used for?

Apache Maven is a build automation and project management tool, primarily used for Java projects. It relies on a central file called pom.xml (Project Object Model).

* Dependency Management: It automatically downloads libraries and plugins (JARs) required by the project from a central repository, so you don't have to manage them manually.

* Standardization: It enforces a standard directory structure (e.g., src/main/java, src/test/java).

* Build Lifecycle: It manages the compilation, testing, packaging, and deployment of code using standard "goals."

4. How does Jenkins use build tools like Maven?
Jenkins acts as the orchestrator, while Maven acts as the worker.

* Jenkins does not know how to compile Java code natively; it delegates that task to Maven.

* Inside a Jenkins job, you configure a "Build Step" that invokes top-level Maven targets.

* Example: You might tell Jenkins to run the command mvn clean install. Jenkins will spin up a workspace, download the code, and then execute that Maven command. Maven handles the compiling and packaging, and reports the success or failure back to Jenkins.

5. What is the difference between compile and package in Maven?
These are two different phases in the Maven Build Lifecycle. The key thing to remember is that the lifecycle is sequential.

6. Where do you configure tools in Jenkins?
You configure global tools (like specific versions of Java, Maven, Git, or Gradle) in the Global Tool Configuration area.
* Path: Dashboard $\rightarrow$ Manage Jenkins $\rightarrow$ Tools (or "Global Tool Configuration" in older versions).
* Usage: Here you can specify the path to where Maven is installed on the Jenkins server (M2_HOME) or tell Jenkins to "Install automatically" whenever a build needs it.

7. How do you debug a failed Jenkins build?
Debugging is a critical skill. The standard workflow is:

    1. Check Console Output: This is the first and most important step. Click the failed build number and select "Console Output." Scroll to the bottom to see the specific error message (e.g., "Compilation failure," "Test failed," or "Connection timed out").

    2. Analyze the Error:

        * Test Failure: Look for which unit test failed and why (assertion error).

        * Build Failure: Look for syntax errors or missing dependencies in the Maven log.

    3.Check the Workspace: Sometimes you need to see if files were actually created. You can browse the "Workspace" link in the job to see the file structure on the server.

    4. Reproduce Locally: If the error isn't obvious, try running the exact same Maven command on your local machine using the same branch. If it works locally but fails on Jenkins, the issue might be environment-related (different Java version, missing credentials, or cached dependencies).