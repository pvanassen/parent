def buildJdk = 'jdk8'
def buildMvn = 'maven'

node {
    stage('Clean') {
        withMaven(jdk: jdkName, maven: mvnName, mavenLocalRepo:"${WORK_DIR}/.repository", options:[
            artifactsPublisher(disabled: false),
            junitPublisher(ignoreAttachments: false),
            findbugsPublisher(disabled: false),
            openTasksPublisher(disabled: false),
            dependenciesFingerprintPublisher(),
            invokerPublisher(),
            pipelineGraphPublisher()
        ]) {
            sh "mvn clean verify -B -U -e -fae -V -Dmaven.test.failure.ignore=true"
        }
    }
}