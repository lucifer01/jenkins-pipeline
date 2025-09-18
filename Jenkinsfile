pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "${WORKSPACE}"
        TESTING_ENVIRONMENT = 'staging'
        PRODUCTION_ENVIRONMENT = 'production'
    }

    triggers {
        pollSCM('H/1 * * * *') // checks on every 1 minute, and builds only if there are changes in git repo
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${env.DIRECTORY_PATH}"
                echo "Build the code using 'Webpack' to compile and package the code."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests using 'Jest' to ensure the code functions as expected."
                echo "Run integration tests using 'Supertest' to verify interactions between components."
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Check the quality of the code using 'ESLint','SonarQube' to ensure it meets industry standards."
            }
        }

        stage('Security Analysis') {
            steps {
                echo "Perform a security scan on the code using 'SonarQube' to identify any vulnerabilities."
            }
        }

        stage('Deploy to staging') {
            steps {
                echo "Deploy the application to ${env.TESTING_ENVIRONMENT} server (AWS EC2 instance) using 'Jenkins'."
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on staging also using 'Cypress' to ensure the app functions as expected."
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the ${env.PRODUCTION_ENVIRONMENT} server (AWS EC2 instance) using 'Jenkins'."
            }
        }
    }
}
