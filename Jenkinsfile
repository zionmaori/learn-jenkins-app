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
                }
            }
            steps {
                sh '''
                ls -la
                    echo "Test Stage"
                    if [ ! -f build/index.html ]; then 
                        echo "file not found!"
                    else
                        echo "file found"
                    fi
                    npm ci
                    npm test

                '''
            }
            
        
        }
    }
}
