pipeline {
    agent any

    environment {
        DIRECTORY_PATH = '/path/to/your/code'  // Define your path here
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh "echo 'Retrieving source code from ${env.DIRECTORY_PATH}' >> test.log"
                    sh "echo 'Compiling the source code and creating necessary artifacts' >> test.log"
                    sh "echo 'Utilizing Maven for build automation' >> test.log"
                    // sh "mvn clean install >> test.log"  // Example Maven command
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    sh "echo 'Executing unit tests' >> test.log"
                    sh "echo 'Running integration tests' >> test.log"
                    sh "echo 'Tools: JUnit for unit testing and Postman for integration testing' >> test.log"
                    // sh "mvn test >> test.log"  // Example Maven test command
                }
            }
            post {
                success {
                    emailext body: "Unit and Integration Tests completed successfully. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Unit and Integration Tests Passed",
                    attachmentsPattern: 'test.log',
                    attachLog: true
                }
                failure {
                    emailext body: "Unit and Integration Tests failed. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Unit and Integration Tests Failed",
                    attachmentsPattern: 'test.log',
                    attachLog: true
                }
            }
        }

        stage('Code Quality Analysis') {
            steps {
                script {
                    sh "echo 'Analyzing code quality' >> test.log"
                    sh "echo 'Using SonarQube Scanner plugin' >> test.log"
                    // sh "sonar-scanner >> test.log"  // Example SonarQube command
                }
            }
        }

        stage('Security Vulnerability Scan') {
            steps {
                script {
                    sh "echo 'Conducting security scan for vulnerabilities' >> test.log"
                    sh "echo 'Using OWASP Dependency-Check plugin' >> test.log"
                    // sh "dependency-check --project Jenkins --scan . >> test.log"  // Example OWASP Dependency-Check command
                }
            }
            post {
                success {
                    emailext body: "Security Scan completed successfully. Logs are attached.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Security Scan Passed",
                    attachmentsPattern: 'test.log',
                    attachLog: true
                }
                failure {
                    emailext body: "Security Scan encountered issues.",
                    to: 'pateldhruvi1279@gmail.com',
                    subject: "Security Scan Failed",
                    attachmentsPattern: 'test.log',
                    attachLog: true
                }
            }
        }

        stage('Deploy to Staging Environment') {
            steps {
                script {
                    sh "echo 'Deploying the application to the staging environment' >> test.log"
                    sh "echo 'Deploying using AWS' >> test.log"
                    // sh "aws deploy start-deployment --application-name MyApp --deployment-group-name MyGroup --s3-location bucket=my-bucket,bundleType=zip,eTag=123456789abcdefg,key=my-app.zip >> test.log"  // Example AWS deployment command
                }
            }
        }

        stage('Integration Testing on Staging') {
            steps {
                script {
                    sh "echo 'Running integration tests on the staging environment' >> test.log"
                    sh "echo 'Utilizing JUnit for testing' >> test.log"
                    // sh "mvn verify >> test.log"  // Example Maven verification command
                }
            }
        }

        stage('Production Deployment') {
            steps {
                script {
                    sh "echo 'Deploying the application to the production environment' >> test.log"
                    sh "echo 'Deploying using AWS' >> test.log"
                    // sh "aws deploy start-deployment --application-name MyApp --deployment-group-name ProdGroup --s3-location bucket=my-bucket,bundleType=zip,eTag=123456789abcdefg,key=my-app.zip >> test.log"  // Example AWS production deployment command
                }
            }
        }
    }

    post {
        always {
            // Archive the test.log so that it's available in the Jenkins build artifacts
            archiveArtifacts artifacts: 'test.log', allowEmptyArchive: true

            // Optional: Send an additional email if needed
            emailext body: "Build ${currentBuild.fullDisplayName} completed. Logs are attached.",
                     to: 'pateldhruvi1279@gmail.com',
                     subject: "Build ${currentBuild.result}",
                     attachmentsPattern: 'test.log',
                     attachLog: true
        }
    }
}
