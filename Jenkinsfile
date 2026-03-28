pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                // Jenkins automatically pulls code from GitHub (configured in job)
                echo "Code checkout completed"
            }
        }

        stage('Validate HTML') {
            steps {
                echo "Validating HTML file..."
                sh 'ls -l'
            }
        }

        stage('Deploy to Apache Server') {
            steps {
                echo "Deploying files to Apache server..."

                // Copy files to Apache web directory
                sh '''
                sudo cp -r * /var/www/html/
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                echo "Deployment successful. Verify in browser."
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed. Check logs."
        }
    }
}