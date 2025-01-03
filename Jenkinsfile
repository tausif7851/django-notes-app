@Library("Shared") _
pipeline{
    
    agent {label "vinod"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/tausif7851/django-notes-app.git","dev")
                }
            }
        }
        stage("Build"){
            steps{
                script(){
                    docker_build("notes-app","latest","tausif7851")
                }
                //              OR
                // echo "This is Building the code"
                // sh "docker build -t notes-app:latest ."
            }
        }
        stage("Push to DockerHub"){
            steps{
                script(){
                    docker_push("notes-app","latest","tausif7851")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
