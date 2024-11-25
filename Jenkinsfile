pipeline{
  agent any
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
}
