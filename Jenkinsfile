pipeline{
    agent { label 'JDK11'}
    stages{
        stage ('Source Code'){
            steps{
                git branch: 'main', url: 'https://github.com/pixelswapnil13/spring-petclinic.git'
            }

        }
        stage ('Build the code'){
            steps{
                sh script: 'mvn clean package'
            } 
        }
        stage ('Running Junit test'){
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }
        stage ('Archive Artifact' ){
            steps{
                archiveArtifacts artifacts: '**/*.jar'
            }
        }
    }
}
//Declarative pipeline