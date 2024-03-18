Jenkinsfile
pipeline {
    agent any 
    stages {
        stage('Docker Build DEV Image') { 
            when {
                branch 'dev'
            }
            steps {
                script {
                echo "Docker DEV image built successfully... Now logging in to Docker Hub and pushing the image."
                def app = docker.build("asfiyask/dev:latest")
                    docker.withRegistry('https://registry.hub.docker.com/asfiyask/dev', 'Dockerhub_creds') {
                        app.push()
                    }
                }
            }
        }
        stage('Docker Build QA Image') { 
            when {
                branch 'qa'
            }
            steps {
                script {
                echo "Docker QA image built successfully... Now logging in to Docker Hub and pushing the image."
                def app = docker.build("asfiyask/qa:latest")
                    docker.withRegistry('https://registry.hub.docker.com/asfiyask/qa', 'Dockerhub_creds') {
                        app.push()
                    }
                }
        
            }

        }
    }
    post { 
        always { 
            echo 'Deleting Project now !! '
            deleteDir()
        }
    
    }
}