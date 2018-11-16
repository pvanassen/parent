pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk8'
    }
    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
    }
}