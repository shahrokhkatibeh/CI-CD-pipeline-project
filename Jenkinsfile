pipeline {
    agent any
    environment {
        VENV_DIR = "venv"
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                git 'https://github.com/shahrokhkatibeh/CI-CD-pipeline-project.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Setting up Python environment...'
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    if [ -f requirements.txt ]; then
                        pip install -r requirements.txt
                    fi
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    . $VENV_DIR/bin/activate
                    if command -v pytest >/dev/null 2>&1; then
                        pytest
                    else
                        echo "pytest not installed, skippin
