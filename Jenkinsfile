pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/hearty101224/ci-cd-automation.git' 
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Python Script') {
            steps {
                sh 'python3 app.py'
            }
        }
        stage('Test Application') {
            steps {
                sh 'pytest test_app.py'
            }
        }
    }
}
