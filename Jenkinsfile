pipeline {
agent any

tools {
    jdk 'JDK21'
}

environment {
    GRADLE_OPTS = "-Dorg.gradle.daemon=false"
}

stages {

    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Prepare') {
        steps {
            script {
                if (isUnix()) {
                    sh 'chmod +x gradlew'
                }
            }
        }
    }

    stage('Build & Test') {
        steps {
            script {
                if (isUnix()) {
                    sh './gradlew clean build'
                } else {
                    bat 'gradlew.bat clean build'
                }
            }
        }
    }
}

post {
    always {
        junit allowEmptyResults: true, testResults: 'build/test-results/test/*.xml'
        archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
        cleanWs()
    }
}

