pipeline {
    agent any

    environment {
        // Define environment variables if needed
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your Git repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm (if not already installed)
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | bash -'
                sh 'apt-get install -y nodejs'

                // Install project dependencies (e.g., npm install)
                sh 'npm install'
            }
        }

        stage('Build SPA') {
            steps {
                // Build your SPA (e.g., npm run build)
                sh 'npm run build'
            }
        }

        stage('Deploy SPA') {
            steps {
                // Copy the built SPA to your deployment location (e.g., a web server)
                // You may need additional steps or scripts here based on your deployment strategy
                sh 'cp -R build/* /var/www/html/my-spa/'
            }
        }
    }

    post {
        success {
            echo 'SPA build and deployment successful!'
        }
        failure {
            echo 'SPA build or deployment failed!'
        }
    }
}
