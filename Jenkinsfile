pipeline {
    agent any
    tools{
        maven 'local_maven'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Your build steps here
                    sh 'mvn clean package'
                }
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    // Build Docker image
                    docker.build("my-tomcat-app")
                }
            }
        }

        stage('Docker Deploy') {
            steps {
                script {
                    // Deploy Docker container
                    docker.image("my-tomcat-app").run("--name=my-tomcat-container -p 8080:8080 -d")
                }
            }
        }
    }
}
