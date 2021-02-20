// This is a declarative Jenkins pipeline script

import java.time.LocalDateTime
import java.time.ZoneId
import java.time.format.DateTimeFormatter


pipeline {
    agent {
        label 'java'
    }
    options {
        ansiColor('xterm')
    }
    environment {
        ORG_GRADLE_PROJECT_buildVersion="${LocalDateTime.now(ZoneId.of('UTC')).format(DateTimeFormatter.ofPattern(/yyyyMMddHHmmss/))}"
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
                    sh "./gradlew jib -Djib.console='plain'"
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
