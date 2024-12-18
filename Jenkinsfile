pipeline{
agent any
   environment{
    Render = 'https://gallery-1-1rtq.onrender.com'
   }
stages{
    stage('Build'){
      steps{
        nodejs('Node'){
          echo 'Building application'
          sh 'npm install'
          
        }
      }
    }
  }
  post{
    success{
      slackSend(
        message: "Build succes."
      )
    }
    failure{
      slackSend(
        message: "Build failed."
      )
    }
    always{
      slackSend(
        message: "Build done. Build Id: ${env.BUILD_ID}. Website at: ${env.Render}"
      )
    }
  }
}