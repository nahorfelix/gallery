pipeline{
agent any
   environment{
    Render = ''
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
}