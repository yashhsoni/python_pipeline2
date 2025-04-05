pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/yashhsoni/python_pipeline2.git'
            }
        }

        stage('Setup Python') {
            steps {
                bat 'python -m venv venv'
                bat '''
                    call venv\\Scripts\\activate
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Python Script') {
            steps {
                bat '''
                    call venv\\Scripts\\activate
                    python app.py
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline Execution Completed.'
        }
    }
}
