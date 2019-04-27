node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        // Add dockerhub name as prefix to container
        app = docker.build('brettgpalmer/example-node-app')
    }

    stage('Push image') {
        // This push process can take several minutes to complete.
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push('latest')
        }
    }
}