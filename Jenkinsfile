pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'kartikey4786.be23@chitkara.edu.in'
        USER_EMAIL = 'kartikey4786.be23@chitkara.edu.in'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean package' // Example for Java apps, use npm/yarn for Node.js
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test' // For Java, use pytest/unittest for Python
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis using SonarQube...'
                sh 'sonar-scanner -Dsonar.projectKey=myproject'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using Snyk...'
                sh 'snyk test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                sh './deploy.sh staging' // Adjust as per your deployment method
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                sh 'mvn verify -Dstaging=true'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                sh './deploy.sh production'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
            mail to: "${USER_EMAIL}",
                 subject: 'Pipeline Execution Successful',
                 body: 'The entire pipeline has completed successfully.'
        }
        failure {
            echo 'Pipeline failed! Check the logs for more details.'
            mail to: "${USER_EMAIL}",
                 subject: 'Pipeline Execution Failed',
                 body: 'The pipeline has failed. Please check the Jenkins logs for more details.'
        }
    }
}
