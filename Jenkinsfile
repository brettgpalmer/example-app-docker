node {
    def app

    stage('Clone repository') {
        check scm
    }

    stage('Build image') {
        # Add dockerhub name as prefix to container
        app = docker.build('brettgpalmer/example-node-app')
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push('latest')
        }
    }
}