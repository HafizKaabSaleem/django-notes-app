@Library("Shared") _
pipeline {
    
    agent { label "vinod" }

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
                 clone("https://github.com/HafizKaabSaleem/django-notes-app","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","kaabsaleem")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","kaabsaleem")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }        
}
