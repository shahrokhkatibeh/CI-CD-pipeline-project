pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Setting up Python virtual environment...'
                // ایجاد virtual environment
                bat 'python -m venv venv'
                // نصب dependencies
                bat '.\\venv\\Scripts\\pip install --upgrade pip'
                bat '.\\venv\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '.\\venv\\Scripts\\python -m unittest discover'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment successful!'
            }
        }
    }
}
