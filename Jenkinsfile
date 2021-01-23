// This is a declarative Jenkins pipeline script

pipeline {
    agent any
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
