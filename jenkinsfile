pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ALACHEMS/Aegis-html.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing npm dependencies...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                // Adjust the path to your build folder
                archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded!'
            // Example: send a Slack notification
            // slackSend(channel: '#dev', message: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}")
        }
        failure {
            echo '❌ Build failed!'
            // Example: send a Slack notification
            // slackSend(channel: '#dev', message: "Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}")
        }
        always {
            echo 'Cleaning workspace...'
            cleanWs()
        }
    }
}


