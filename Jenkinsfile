pipeline {
    agent any
    stages {
        stage('切换Node环境') {
            steps {
                sh '''
                    #!/bin/bash
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    nvm use 20
                    node -v
                    npm -v
                '''
            }
        }
}

