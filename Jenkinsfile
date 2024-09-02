pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
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
        stage('Test') {
            agent {
                docker {
                    image 'node:19-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    test -f build/index.html
                    npm test

                '''
            }
            
        
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
