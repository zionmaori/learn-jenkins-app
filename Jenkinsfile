pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker {
                    image 'mode:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''

            }
        }
    }
}
