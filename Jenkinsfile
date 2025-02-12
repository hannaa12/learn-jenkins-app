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
                    echo "Cleaning old dependencies..."
                    rm -rf node_modules package-lock.json

                    echo "Clearing NPM cache..."
                    npm cache clean --force

                    echo "Installing dependencies..."
                    npm install --legacy-peer-deps

                    echo "Building the project..."
                    npm run build

                    echo "Build completed successfully."
                '''
            }
        }
    }
}
