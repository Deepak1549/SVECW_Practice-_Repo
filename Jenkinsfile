pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/registration-cicd.git'
            }
        }

        stage('Validate HTML') {
            steps {
                sh '''
                    echo "Checking if registration.html exists..."
                    if [ -f registration.html ]; then
                        echo "File found. Validation passed."
                    else
                        echo "ERROR: registration.html not found!"
                        exit 1
                    fi
                '''
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sh '''
                    echo "Deploying registration.html to Apache..."
                    sudo cp registration.html /var/www/html/registration.html
                    echo "Deployment successful!"
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -s -o /dev/null -w "%{http_code}" http://localhost/registration.html'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! Registration page is live.'
        }
        failure {
            echo 'Pipeline failed. Check the logs above.'
        }
    }
}

