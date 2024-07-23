pipeline {
  agent any
  stages{
    stage('Build'){
      steps{
        sh 'sudo npm install -g'
      }      
    }

    stage('Deploy'){
      steps{
        sh 'npm run start:dev'
      }      
    }

  }
}
