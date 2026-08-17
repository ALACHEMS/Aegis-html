pipeline {
    agent any

    tools {
        nodejs 'Node26.7'
    }


    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }


        stage('Build') {
            steps {
                echo 'Building application...'
               
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: '**/dist/**', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }

        failure {
            echo '❌ Build failed!'
        }

        always {
            echo 'Cleaning workspace...'
            cleanWs()
        }
    }
}
