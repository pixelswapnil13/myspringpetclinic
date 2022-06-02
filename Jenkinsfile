pipeline{
    agent { label 'JDK11'}
    stages{
        stage ('Source Code'){
            steps{
                git branch: 'feature_declarative', url: 'https://github.com/pixelswapnil13/myspringpetclinic.git'
            }
        }
        stage ('Build the code'){
            withSonarQubeEnv('SONAR_LATEST') {
                    sh script: "mvn package sonar:sonar"
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