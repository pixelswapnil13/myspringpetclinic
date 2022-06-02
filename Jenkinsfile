pipeline{
    agent { label 'JDK11'}
    stages{
        stage ('Source Code'){
            steps{
                git branch: 'feature_declarative', url: 'https://github.com/pixelswapnil13/myspringpetclinic.git'
            }
        }
        stage ('Build the Code and sonarqube-analysis'){
            steps {
                withSonarQubeEnv('SONAR_8.9') {
                    sh script: "mvn package sonar:sonar"
                  }
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