pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh 'echo checkout'
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hysenelv/DevOpsDemoEH.git']])
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
                dir('backend') {
                    sh 'chmod +x gradlew'
                    sh './gradlew test'
                }
                jacoco()
                    
                
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo deploy'
            }
        }
    }
}
