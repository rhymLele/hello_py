pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Lấy mã nguồn từ repository
                git 'https://github.com/rhymLele/hello_py.git'
            }
        }
        stage('Install Node.js and npm') {
            steps {
                // Kiểm tra và cài đặt Node.js và npm nếu cần thiết
                sh '''
                    if ! command -v npm &> /dev/null
                    then
                        curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
                        sudo apt install -y nodejs
                    fi
                    node -v
                    npm -v
                '''
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
