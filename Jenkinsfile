node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
        app = docker.build("malevs/part3")
    }
    stage('Push image') {   
        docker.withRegistry('https://hub.docker.com/r/malevs/part3', 'dockerhub') {
            dockerImage.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            dockerImage.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
