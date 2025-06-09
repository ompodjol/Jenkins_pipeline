// Jenkinsfile
pipeline {
    agent any
    parameters {
        choice(
            name: 'DEPLOY_TARGET',
            choices: ['dev', 'staging', 'production', 'qa', 'testing'],
            description: 'Select the deployment environment'
        )
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Deploy to Dev') {
            when {
                expression { params.DEPLOY_TARGET == 'dev' }
            }
            steps {
                echo "Deploying to the development environment (${params.DEPLOY_TARGET})"
                // Add your dev deployment steps here
            }
        }

        if (params.DEPLOY_TARGET == 'staging') {
            stage('Deploy to Staging') {
                when {
                    expression { params.DEPLOY_TARGET == 'staging' }
                }
                steps {
                    echo "Deploying to the staging environment (${params.DEPLOY_TARGET})"
                    // Add your staging deployment steps here
                }
            }
        }

        stage('Deploy to Production') {
            when {
                expression { params.DEPLOY_TARGET == 'production' }
            }
            steps {
                echo "Deploying to the production environment (${params.DEPLOY_TARGET})"
                // Add your production deployment steps here
            }
        }

        stage('Run QA Tests') {
            when {
                expression { params.DEPLOY_TARGET == 'qa' || params.DEPLOY_TARGET == 'testing' }
            }
            steps {
                echo "Running QA tests for target: ${params.DEPLOY_TARGET}"
                // Add your QA test steps here
            }
        }

        // Add more stages as needed, each with its own 'when' condition
    }
}
