
# Jenkins CI/CD Pipeline with Java Program

### **Project Overview**
This project demonstrates a Jenkins CI/CD pipeline to automate the process of building, testing, and deploying a Java program. The pipeline integrates source control, automated build tools, and execution steps, showcasing the power of continuous integration and deployment.

## **Guidance**
**Dr. Santosh Kumar**

---

## **Group Members**
| Member Name         | GitHub                                          | Email                                                |
|---------------------|---------------------------------------------    |------------------------------------------------------|
| **Kalyani Bonde**   | [Kalyanibonde](https://github.com/Kalyanibonde) | kalyani.22320196@gmail.com / kalyanibonde05@gmail.com|
| **Riya Shete**      | https://github.com/riyashete19)                 | riya.22320173@viit.ac.in                             |
| **Aryan Dalvi**     | [Aryanr34](https://github.com/Aryanr34)         | aryan.22210619@viit.ac.in                            |
| **Aditya Jasoriya** | [Aditya01229](https://github.com/Aditya01229)   | aditya.22210607@viit.ac.in                           |

---

## **Project Setup**

### **1. Starting the Jenkins Server**
1. Navigate to the Jenkins installation directory:
 cd "C:\Program Files\Jenkins"
Start the server using the following command:
java -jar jenkins.war --httpPort=8181
Open a browser and go to:
http://localhost:8181
Log in to the Jenkins web interface using your credentials.

2. Setting Up the Workspace
Jenkins stores program files in:
C:\Users\<username>\.jenkins\workspace
Example directory for a Java program:
C:\Users\kalya\.jenkins\workspace\task1\first.java

3. Creating the Pipeline

Step 1: Create a New Job
Navigate to the Jenkins Dashboard:
http://localhost:8181
Click on "New Item".
Provide a name for your pipeline and select Pipeline as the project type.
Click OK.

Step 2: Configure the Pipeline
In the General Settings, add a description (optional).
Configure source code management (e.g., Git) if needed.
In the Pipeline section:
Select Pipeline script in the Definition dropdown.
Enter the following pipeline script:

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/your-repository/java-project.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Java project...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }

        stage('Execute') {
            steps {
                echo 'Executing the Java program...'
                sh 'java -jar target/your-program.jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed!'
        }
    }
}

4. Running the Pipeline
Save Configuration:
Click Save after entering the pipeline script.

Build the Pipeline:
On the pipeline dashboard, click Build Now.
Jenkins will execute the pipeline steps.

Monitor Progress:
Navigate to the Build History section on the left.
Click on the latest build number to view the Console Output and monitor logs.

## **Key Points**
Simple Setup: No need for external Jenkinsfiles or additional configurations.
Live Output: Observe the pipeline progress directly from the interface.
Post-Build Actions: Configure additional steps like artifact archiving or notifications.

## **Additional Notes:**
Install Required plugins : pipeline plugin (depends on project execution for html: HTML publisher plugin)
Tools Configuration
Ensure the following tools are installed and configured under Manage Jenkins > Global Tool Configuration:
JDK
Maven

## **References**
Jenkins Documentation: Jenkins.io

Maven Documentation: Maven.apache.org
