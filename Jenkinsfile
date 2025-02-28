pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
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
                ls -la
                '''
            }
        }
        stage('Test'){
            steps{
                sh '''
                echo "Test Stage"
                test -f build/index.html && echo "Index File exists" || echo "Index File not found"
                npm test
                '''
            }
            
        }
    }
}