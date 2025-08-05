pipeline {
    agent any

    stages {
        stage('build') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh '''
                    echo "listing files in directory"
                    ls -la
                    echo "node version: "
                    node --version
                    echo "npm version: "
                    npm --version
                    npm ci
                    npm run build
                    echo "what we have after build: "
                    ls -la
               '''
            }
        }
        stage('Test'){

            steps{
                sh '''
                    test -f build/index.html
                '''
            }
        
        }
    }


}
