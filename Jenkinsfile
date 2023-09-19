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
                cleanWs()
            }
            
        }
        stage("Checkout from SCM"){
            steps{
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/h4nz0x/Java-app-with-E2E-CI-CD'
            }
            
        }
        stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
            
        }
        stage("Test Application"){
            steps{
                sh "mvn test"
            }
            
        }
        stage("SonarQube Analysis"){
            steps{
                script {
                    withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token'){
                        sh "mvn sonar:sonar"
                }
                }
            }
            
        }
    }
    
}