// This is a declarative Jenkins pipeline script

pipeline {
    agent {
        label 'java'
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Build') {
            steps {
                sh "./gradlew build"
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'jenkins-harbor', passwordVariable: 'HARBOR_PASSWORD', usernameVariable: 'HARBOR_USER')]) {
                    sh "./gradlew jib"
                }
            }
        }
    }
    post {
        cleanup {
            deleteDir()
        }
    }
}
