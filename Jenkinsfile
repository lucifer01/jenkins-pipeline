pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "${WORKSPACE}"
        TESTING_ENVIRONMENT = 'testing'
        PRODUCTION_ENVIRONMENT = 'sumit-adhikari'
    }

    triggers {
        pollSCM('H/1 * * * *') // checks on every 1 minute, and builds only if there are changes in git repo
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${env.DIRECTORY_PATH}"
                echo 'Compile the code and generate any necessary artefacts'
            }
        }

        stage('Test') {
            steps {
                echo 'Unit tests'
                echo 'Integration tests'
            }
        }

        stage('Code Quality Check') {
            steps {
                echo 'Check the quality of the code'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy the application to ${env.TESTING_ENVIRONMENT} environment"
            }
        }

        stage('Approval') {
            steps {
                echo 'Waiting for manual approval (10s)...'
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the ${env.PRODUCTION_ENVIRONMENT} environment"
            }
        }
    }
}
