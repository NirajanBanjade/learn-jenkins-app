pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "📦 Installing dependencies..."
                    npm ci

                    echo "🏗️  Building project..."
                    npm run build

                    echo "📁 Contents after build:"
                    ls -la
                '''
            }
        }

        stage('test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "✅ Running tests..."
                    npm test
                '''
            }
        }
    }
}
