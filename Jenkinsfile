pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-u root:root'
        }
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/ljqnicole/simple-node-js-react-npm-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }

        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
