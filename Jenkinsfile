pipeline {
    agent any
    stages {
        // 1. 拉取GitHub代码
        stage('拉取代码') {
            steps {
                git url: '【替换成你的GitHub仓库地址】', credentialsId: '【替换成Jenkins凭证ID】'
            }
        }

        // 2. 切换Node版本（测试用，这里用Node20，想换10就改10）
        stage('切换Node环境') {
            steps {
                sh '''
                    # 加载nvm（必须加，否则Jenkins找不到nvm）
                    source /root/.nvm/nvm.sh
                    # 切换Node 20（老项目改 nvm use 10）
                    nvm use 20
                    node -v
                    npm -v
                '''
            }
        }

        // 3. 部署到Nginx（纯静态项目，直接复制）
        stage('部署到Nginx') {
            steps {
                sh '''
                    # 创建部署目录（不存在则自动创建）
                    mkdir -p /usr/share/nginx/html/vue-test
                    # 复制所有文件到Nginx目录
                    cp -r ./* /usr/share/nginx/html/vue-test/
                '''
            }
        }
    }
    // 构建成功提示
    post {
        success {
            echo '=================================================='
            echo '✅ Vue项目部署完成！访问：服务器IP/vue-test'
            echo '=================================================='
        }
    }
}

