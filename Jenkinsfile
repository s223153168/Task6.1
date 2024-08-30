pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Retrieving source code from ${env.DIRECTORY_PATH}"
                echo "Compiling the source code and creating necessary artifacts"
                echo "Utilizing Maven for build automation"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Executing unit tests"
                echo "Running integration tests"
                echo "Tools: JUnit for unit testing and Postman for integration testing"
            }
            post {
                success {
                    emailext body: "Unit and Integration Tests completed successfully. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Unit and Integration Tests Passed",
                    //attachmentsPattern: 'test.log',
                    //attachLog: true
                }
                failure {
                    emailext body: "Unit and Integration Tests failed. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.comcom',
                    subject: "Unit and Integration Tests Failed",
                    //attachmentsPattern: 'test.log',
                    //attachLog: true
                }
            }
        }

        stage('Code Quality Analysis') {
            steps {
                echo "Analyzing code quality"
                echo "Using SonarQube Scanner plugin"
            }
        }

        stage('Security Vulnerability Scan') {
            steps {
                echo "Conducting security scan for vulnerabilities"
                echo "Using OWASP Dependency-Check plugin"
            }
            post {
                success {
                    emailext body: "Security Scan completed successfully. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Security Scan Passed",
                    //attachmentsPattern: 'test.log',
                    //attachLog: true
                }
                failure {
                    emailext body: "Security Scan encountered issues.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Security Scan Failed",
                    //attachmentsPattern: 'test.log',
                    //attachLog: true
                }
            }
        }

        stage('Deploy to Staging Environment') {
            steps {
                echo "Deploying the application to the staging environment"
                echo "Deploying using AWS"
            }
        }

        stage('Integration Testing on Staging') {
            steps {
                echo "Running integration tests on the staging environment"
                echo "Utilizing JUnit for testing"
            }
        }

        stage('Production Deployment') {
            steps {
                echo "Deploying the application to the production environment"
                echo "Deploying using AWS"
            }
        }
    }
}
