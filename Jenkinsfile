pipeline {
 agent{ label 'controlnode' }
//  triggers {
//         cron('0 * * * *')
//     }
 stages{
    stage('Source Code') {
       steps{
           git url: 'https://github.com/pixelswapnil13/myspringpetclinic.git',
           branch: 'main'
        }
    }
    stage('Build the code ans SonarQube Analysis'){
        steps{ 
            withSonarQubeEnv('SONAR_8.9'){
                sh script: "mvn clean package sonar:sonar"
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