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
                   sh 'ls -la'
                   sh 'node --version'
                   sh 'npm --version'
                   sh 'npm ci'
                   sh 'npm run build'
            }
       
        }
        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh 'echo "Test Stage"'
                sh 'test -f build/index.html'
                sh 'npm test'
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
