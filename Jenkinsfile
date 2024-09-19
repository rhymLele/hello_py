pipeline {
    agent any

    environment {
        PYTHON_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                // Lấy mã nguồn từ repository
                git 'https://github.com/username/my-python-app.git'
            }
        }

        stage('Setup Python') {
            steps {
                // Thiết lập môi trường Python
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Cài đặt các package cần thiết
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                // Chạy kiểm thử với pytest
                sh '. venv/bin/activate && pytest'
            }
        }

        stage('Deploy') {
            steps {
                // Triển khai ứng dụng lên máy chủ hoặc môi trường staging
                echo 'Triển khai ứng dụng...'
            }
        }
    }

    post {
        always {
            // Lưu kết quả kiểm thử
            archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
        }

        success {
            // Thông báo khi kiểm thử thành công
            echo 'Build và kiểm thử thành công!'
        }

        failure {
            // Thông báo khi kiểm thử thất bại
            echo 'Build hoặc kiểm thử thất bại!'
        }
    }
}
