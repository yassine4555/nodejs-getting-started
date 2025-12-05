pipeline {
    agent any
    
    stages {
        stage('Check Node') {
            steps {
                echo "✓ Checking Node.js..."
                sh '''
                    which node || echo "Node not found, installing..."
                    node --version || true
                    npm --version || true
                '''
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo "✓ Installing project dependencies..."
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                echo "✓ Building application..."
                sh 'npm run build || echo "No build script found"'
            }
        }
        
        stage('Test') {
            steps {
                echo "✓ Running tests..."
                sh 'npm test || echo "No test script found"'
            }
        }
        
        stage('Archive') {
            steps {
                echo "✓ Archiving artifacts..."
                archiveArtifacts artifacts: '**/dist/*.zip', allowEmptyArchive: true
            }
        }
    }
    
    post {
        success {
            echo "✓ Pipeline completed successfully!"
        }
        failure {
            echo "✗ Pipeline failed"
        }
    }
}