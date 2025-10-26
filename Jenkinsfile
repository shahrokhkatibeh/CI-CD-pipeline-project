pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Setting up Python environment...'
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                . venv/bin/activate
                pytest -v
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment successful!'
            }
        }
    }
}
