pipeline {
    agent any  // Runs on any available Jenkins agent

    environment {
        GITHUB_CREDENTIALS_ID = 'github-credentials' // Ensure this is set in Jenkins credentials
        REPO_URL = 'https://github.com/hearty101224/ci-cd-automation.git'
        BRANCH_NAME = 'main'
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    checkout scmGit(
                        branches: [[name: "${BRANCH_NAME}"]],
                        userRemoteConfigs: [[
                            url: "${REPO_URL}",
                            credentialsId: "${GITHUB_CREDENTIALS_ID}"
                        ]]
                    )
                }
            }
        }

        stage('Setup Python Environment') {
            steps {
                script {
                    // Ensure Python is installed and install dependencies
                    sh 'python --version || python3 --version'
                    sh 'pip install -r requirements.txt || pip3 install -r requirements.txt'
                }
            }
        }

        stage('Run Unit Tests') {
            steps {
                script {
                    // Run Python unit tests
                    sh 'pytest tests/ --junitxml=report.xml'
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    echo "Building and Deploying Application..."
                    sh 'python app.py || python3 app.py'  // Adjust based on OS
                }
            }
        }

        stage('Post-Build') {
            steps {
                echo 'Build completed successfully!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed! Check logs for errors.'
        }
    }
}
