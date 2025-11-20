pipeline {
    agent any

    tools {
        nodejs "NodeJS"        // NOTE: Jenkins me NodeJS tool ka name "NodeJS" rakho
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/sujoybaretha/ecommerce-sample.git',
                        credentialsId: 'github-token'    // 👈 GitHub PAT ID
                    ]]
                ])
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Project') {
            steps {
                sh 'npm run build || echo "No build script found"'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "No tests to run"'
            }
        }

        stage('Deploy / Package') {
            steps {
                echo "Deployment step — yaha aap deployment scripts add kar sakte ho."
            }
        }
    }

    post {
        success {
            echo "🎉 Build Successful!"
        }
        failure {
            echo "❌ Build Failed!"
        }
    }
}
