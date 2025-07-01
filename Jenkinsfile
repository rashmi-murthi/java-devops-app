pipeline{
    agent any
    stages{
        stage("code"){
            steps{
                echo "cloning the code"
                git branch: 'main', url: 'https://github.com/rashmi-murthi/java-devops-app.git'
            }
        }
        stage("maven unit test"){
            steps{
                sh "mvn test"
            }
        }
        stage("maven integration test"){
            steps{
                sh "mvn verify"
            }
        }
        stage("build docker image"){
            steps{
                echo "build the docker image"
                sh "docker build -t java-devops-app ."
            }
        }
        stage("run container"){
            steps{
                echo "running container inside docker"
                sh "docker stop java-devops-container || true"
                sh "docker rm java-devops-container || true"
                sh "docker run -d --name java-devops-container -p 8081:8081 java-devops-app"
            }
        }
    }
}
