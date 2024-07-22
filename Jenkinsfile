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
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }
}
