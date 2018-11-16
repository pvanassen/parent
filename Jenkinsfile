pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk8'
    }
    triggers {
        pollSCM('* * * * *')
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
            parallel {
                stage ('Deploy snapshot') {
                    when {
                        not {
                            branch 'master'
                        }
                    }
                    steps {
                        sh 'mvn deploy'
                    }
                }

                stage ('Deploy master') {
                    when {
                        branch 'master'
                    }
                    steps {
                        sh 'mvn deploy -Psonatype-oss-release'
                    }
                }
            }
        }
    }
}