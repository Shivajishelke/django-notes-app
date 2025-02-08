@Library('Shared')_
pipeline{
    agent { label 'vinod'}
    
    stages{
        stage("Code clone"){
            steps{
                 script
                    {
                        clone("https://github.com/Shivajishelke/django-notes-app.git","main")
                    }
            }    
        }
        stage("Code Build"){
            steps{
                script{ docker_build("notes-app","latest")}
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{

                docker_push("DockerCred","notes-app","latest")
                }
                }
        }
        stage("Deploy"){
            steps{
                deploy()
            }
        }
        
    }
}
