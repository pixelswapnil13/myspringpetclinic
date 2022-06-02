pipeline {
 agent{ label 'JDK11' }
//  triggers {
//         cron('0 * * * *')
//     }
 stages{
    stage('Source Code') {
       steps{
           git branch: 'main', url: 'https://github.com/pixelswapnil13/spring-petclinic.git' 
        }
    }
    stage('Build the code ans SonarQube Analysis'){
        steps{ 
            withSonarQubeEnv('SONAR_8.9'){
                sh 'mvn clean package sonar:sonar'
            }  
        }
    }
    stage('Junit Test'){
        steps{
            junit '**/surefire-reports/*.xml'
        }
    }
    stage('Archive artifact'){
        steps{
           archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
        }
    }
  }
}