pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "${WORKSPACE}"
        TESTING_ENVIRONMENT = 'testing'
        PRODUCTION_ENVIRONMENT = 'sumit-adhikari'
    }
    {
        triggers: {
            pollSCM('H/5 * * * *') // runs every 5 minutes when there are changes in the git repository (SCM)
        }
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${DIRECTORY_PATH}"
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
                echo "Deploy the application to ${TESTING_ENVIRONMENT} environment"
            }
        }

        stage('Approval') {
            steps {
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the production environment: ${PRODUCTION_ENVIRONMENT} environment"
            }
        }
    }
}
