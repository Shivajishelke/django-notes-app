@Library("Shared") _
pipeline
{
    agent {label 'vinod'}
    stages
    {
        stage("Hello")
        {
            steps
            {
                script
                {
                    hello()
                }
            }
        }
        stage("Code Clone")
        {
            steps
            {
            echo "This is for code clone"
            git url: "https://github.com/Shivajishelke/django-notes-app.git", branch: "main"
            echo "Successful"
            
            }   
        }
        stage("Code build")
        {
            steps
            {
                echo "This is for build"
                sh "docker build -t notes-app:latest1 ."
            }
        }
        stage("Push to DockerHub")
        {
            steps
            { 
                script
                {
                    docker_push("notes-app", "latest1", "shiivajishelke14")
                }
            }
        }
        stage("Code Deploy")
        {
            steps
            {
                echo "This is for Deploy"
                sh "docker run -d -p 8000:8000 notes-app:latest1"
            
            }
        }
    }
}
