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
    }
    post {
        cleanup {
            deleteDir()
        }
    }
}
