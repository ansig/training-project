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
        ORG_GRADLE_PROJECT_buildVersion="${LocalDateTime.now(ZoneId.of('UTC')).format(DateTimeFormatter.ofPattern(/yyyyMMdd-HHmmss/))}"
    }
    stages {
        stage('Prepare') {
            steps {
                script {
                    def props = readProperties file: 'gradle.properties'
                    currentBuild.description = "${props.baseVersion}-${env.ORG_GRADLE_PROJECT_buildVersion}"
                }
            }
        }
        stage('Build') {
            steps {
                sh "./gradlew build"
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'jenkins-ecr', passwordVariable: 'ECR_PASSWORD', usernameVariable: 'ECR_USER')]) {
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
