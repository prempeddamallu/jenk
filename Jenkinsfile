pipeline {
    agent any

    environment {
        DEPLOY_ENV = 'production'  // Define the environment variable
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the project..."
                    // sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests..."
                    // sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'  // Only deploy on the 'main' branch
            }
            steps {
                script {
                    echo "Deploying to ${env.DEPLOY_ENV}..."  // Correctly reference the environment variable
                    // sh './deploy.sh'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    echo "Cleaning up..."
                    // sh 'rm -rf target/'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment succeeded!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
        always {
            echo 'This will always run, regardless of the build result.'
        }
    }
}
