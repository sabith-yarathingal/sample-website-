pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sabith-yarathingal/sample-website-.git'
            }
        }

        stage('Build/Validate') {
            steps {
                echo "Checking for HTML files..."
                sh 'ls -l *.html || echo "No HTML found!"'
            }
        }

        stage('Deploy to Apache') {
            steps {
                echo "Deploying website to Apache server..."
                // copy website files to Apache web root
                sh 'sudo cp -R * /var/www/html/'
            }
        }
    }

    post {
        success {
            echo "Website successfully deployed!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
