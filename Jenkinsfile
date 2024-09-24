pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                git 'https://github.com/Toan211203/emo2_jenkin.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'python3 hello3.py'  // Sử dụng python3
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                script {
                    if (fileExists('hello.py')) {
                        echo 'File hello.py found. Displaying its content:'
                        
                        // Đọc nội dung file hello.py và in ra console
                        def content = readFile('hello.py')
                        echo "${content}"
        
                        // Chạy script hello.py và in ra đầu ra
                        echo 'Running the script...'
                        def output = sh(script: 'python3 hello.py', returnStdout: true).trim()
                        echo "Output from hello.py: ${output}"
                    } else {
                        error 'File hello.py does not exist!'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Thêm lệnh deploy ở đây
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
        always {
            echo 'Cleaning up...'
            // Thêm lệnh dọn dẹp nếu cần
        }
    }
}