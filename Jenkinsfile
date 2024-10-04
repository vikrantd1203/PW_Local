
pipeline {
    agent any
    tools {
        nodejs "nodejs-playwright"
    }

    stages {
        stage('setup1') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9', localConfig: [localOptions: '--force-local', localPath: '']) {
                    echo 'First Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'First Completed'
                }
            }
        }
        stage('setup2') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    echo 'Second Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Second Completed'
                }
            }
        }
        stage('setup3') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    echo 'Third Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Third Completed'
                }
            }
        }
    }
    post {
        always {
            script {
                // Stop BrowserStack Local after the tests
                echo 'Stopping BStack Binary'
                sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon stop'
            }
        }
    }
}