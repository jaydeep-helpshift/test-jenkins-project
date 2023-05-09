pipeline {
    agent any
    stages {
        stage('Fetch code') {
            steps {
                git branch: 'main', url: 'https://github.com/jaydeep-helpshift/test-jenkins-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'make build'
            }
            
            post {
                success {
                    echo 'Now Archiving it...'
                    archiveArtifacts artifacts: '**/artifact'
                }
            }
        }
        
        stage('UNIT TEST') {
            steps {
                sh 'make test'
            }
        }
    }
}