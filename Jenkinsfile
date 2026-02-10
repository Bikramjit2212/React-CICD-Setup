pipeline {
    agent any
    stages {
        stage('build'){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true //reuse the node for the next stages
                }
            }

            steps {
                sh '''
                    ls -l
                    node --version
                    npm --version
                    npm install
                    npm run build
                '''
            }
        }
    }
}