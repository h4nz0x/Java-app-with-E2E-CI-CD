pipeline{
    agent{
        label "jenkins-agent-docker"
    }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    stages{
        stage("CleanUp Workspace"){
            steps{
                cleanW()
            }
            
        }
        stage("Checkout from SCM"){
            steps{
                git branch: 'main', credentialsId: 'github' url: 'https://github.com/h4nz0x/Java-app-with-E2E-CI-CD'
            }
            
        }
    }
    
}