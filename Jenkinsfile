pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk8'
    }
    triggers {
        pollSCM('0 0 * * 0')
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
        }

        stage ('Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}