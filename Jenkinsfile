pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR-USERNAME/ci-cd-automation.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    def python = tool 'Python3'
                    sh "${python}/bin/python -m pip install pytest"
                }
            }
        }
        stage('Test') {
            steps {
                sh 'pytest test_app.py'
            }
        }
    }
}
