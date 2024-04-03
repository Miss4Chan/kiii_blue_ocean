node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("miss4chan/kiii_blue_ocean")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.docker.io', '0edc376d-f290-4b3e-afbc-bbf02ba8f6aa') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
