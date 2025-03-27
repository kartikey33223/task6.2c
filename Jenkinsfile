pipeline {
    agent any
    
    environment {
        EMAIL_RECIPIENT = 'kartikey4786.be23@chitkara.edu.in'
        USER_EMAIL = 'kartikey4786.be23@chiutkara.edu.in'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Build Stage Completed',
                         body: 'The build stage has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Unit and Integration Tests Completed',
                         body: 'The unit and integration tests have completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Code Analysis Completed',
                         body: 'The code analysis stage has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Security Scan Completed',
                         body: 'The security scan has completed. Check the Jenkins logs for details.'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Deployment to Staging Completed',
                         body: 'Deployment to the staging environment has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Integration Tests on Staging Completed',
                         body: 'Integration tests on staging have completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Deployment to Production Completed',
                         body: 'Deployment to production has completed. Check Jenkins logs for details.'
                }
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

