// This is a declarative Jenkins pipeline script

pipeline {
    agent {
        label 'java'
    }
    stages {
        stage('Build') {
            steps {
                sh "./gradlew build"
            }
        }
        stage('Push') {
            steps {
                sh "./gradlew jib"
            }
        }
    }
    post {
        cleanup {
            deleteDir()
        }
    }
}
