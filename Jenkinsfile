pipeline {
    agent any

    tools {
        // Matches the name configured in Jenkins -> Manage Jenkins -> Tools
        maven 'Maven' 
    }

    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Deployment Version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the testing stage?')
    }

    environment {
        // Global variable accessible in all stages
        NEW_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Muhammad Shahzaib (23i-2083) - Lab 12 Build Initiated' [cite: 13]
                echo "Building version ${NEW_VERSION}" [cite: 619]
                // Windows-specific execution command
                bat "mvn -version" [cite: 637]
            }
        }

        stage('Test') {
            when {
                // Evaluates the boolean parameter [cite: 474]
                expression { params.executeTests } [cite: 692, 694]
            }
            steps {
                echo 'Testing Project...' [cite: 703]
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Project...' [cite: 428]
                echo "Deploying selected version: ${params.VERSION}" 
            }
        }
    }

    post {
        always {
            // Executes regardless of build status [cite: 444]
            echo 'Post build condition running' [cite: 445]
        }
        failure {
            // Executes only if a stage fails [cite: 450]
            echo 'Post action if Build Fails' [cite: 451]
        }
    }
}
