pipeline {
    agent any

    tools {
        // This MUST match the exact name you set in Jenkins -> Manage Jenkins -> Tools
        maven 'Maven' 
    }

    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Deployment Version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the testing stage?')
    }

    environment {
        // Global variable for the pipeline
        NEW_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Muhammad Shahzaib (23i-2083) - Lab 12 Build Initiated'
                echo "Building version ${NEW_VERSION}"
                // A safe Windows command to verify the tool works
                bat "mvn -version"
            }
        }

        stage('Test') {
            when {
                // Now properly populated to check your parameter
                expression { params.executeTests }
            }
            steps {
                echo 'Testing Project...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Project...'
                echo "Deploying selected version: ${params.VERSION}" 
            }
        }
    }

    post {
        always {
            echo 'Post build condition running'
        }
        failure {
            echo 'Post action if Build Fails'
        }
    }
}
