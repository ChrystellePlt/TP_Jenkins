node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("chrysplt/docker-jenkins:${env.BUILD_ID}")
    }

    stage('test') {
        app.inside() {
            env.NODE_ENV = "test"
            sh 'npm prune'
            sh 'npm install'
            sh 'npm test'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'eemi-devops-dockerhub') {
            app.push()
        }
    }
}