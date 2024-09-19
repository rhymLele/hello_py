pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Lấy mã nguồn từ repository
                git 'https://github.com/rhymLele/hello_py.git'
            }
        }

        stage('Lint HTML & CSS') {
            steps {
                // Kiểm tra cú pháp của HTML và CSS
                sh '''
                    # Cài đặt công cụ kiểm tra cú pháp nếu cần (chỉ thực hiện một lần)
                    npm install -g htmlhint csslint
                    # Kiểm tra cú pháp HTML
                    htmlhint index.html
                '''
            }
        }

        stage('Deploy') {
            steps {
                // Triển khai các file lên môi trường (ví dụ: server hoặc cloud)
                echo 'Đang triển khai các file HTML và CSS...'
                // Lệnh triển khai cụ thể (ví dụ: SCP, rsync, hoặc deploy đến một hosting service)
                sh '''
                    scp -r ./index.html ./styles.css user@server:/path/to/deploy
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline thành công! HTML và CSS đã được kiểm tra và triển khai.'
        }
        failure {
            echo 'Pipeline thất bại! Có lỗi trong quá trình kiểm tra hoặc triển khai.'
        }
    }
}
