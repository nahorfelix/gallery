pipeline{
  agent any
  environment{
    Website='https://gallery-608m.onrender.com'
  }
  stages{
    stage('Build'){
      steps{
        nodejs('NodeJs'){
          echo 'Building application'
          sh 'npm install'
          
        }
      }
    }
  }
  post{
    success{
      slackSend(message: "we are live at ${env.Website} ${env.BUILD_ID}")
    }
    failure{
      slackSend(message: " sorry we will be back ${env.Website} ${env.BUILD_ID}")
    }
    always{
      slackSend(message: " thanks  ${env.Website} ${env.BUILD_ID}")
    }
  }
}
