pipeline {
    agent any  // Runs on any available Jenkins agent

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/hearty10122a/ci-cd-automation.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                script {
                    // Check Python version to ensure it's installed
                    sh 'python --version || python3 --version'
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    // Run the Python script
                    sh 'python app.py || python3 app.py' // Adjust based on OS
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
