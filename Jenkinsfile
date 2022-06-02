pipeline {
 agent{ label 'JDK11' }
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
              sh script: "mvn clean package"
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