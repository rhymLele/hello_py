pipeline {
    agent any

    environment {
        PYTHON_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/rhymLele/hello_py.git'
            }
        }

        stage('Setup Python') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate'
            }
        }

        stage('Install Dependencies') {
            steps {
             
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
            
                sh 'pytest'
            }
        }

        stage('Deploy') {
            steps {
        
                echo 'Triển khai ứng dụng...'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
        }

        success {
            echo 'Build và kiểm thử thành công!'
        }

        failure {
            echo 'Build hoặc kiểm thử thất bại!'
        }
    }
}

