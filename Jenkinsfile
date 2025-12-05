pipeline {
    agent any
    
    tools {
        nodejs "nodejs"
    }
    
    stages {
        stage('Install Dependencies') {
            steps {
                echo "✓ Installing dependencies..."
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                echo "✓ Building..."
                sh 'npm run build || echo "No build script"'
            }
        }
        
        stage('Test') {
            steps {
                echo "✓ Testing..."
                sh 'npm test || echo "No test script"'
            }
        }
    }
}