node {
    stage('Clean') {
        mvn clean
    }
    stage('Compile') {
        mvn test
    }
    stage('Test') {
        mvn test
    }
    stage('Install') {
        mvn install
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}