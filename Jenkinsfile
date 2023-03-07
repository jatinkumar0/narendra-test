pipeline {
agent any
  stages {
    stage ('Build'){
      steps {
      sh ''' 
      npm install
      '''
      }
      }
    
      stage ('Deploy'){
      steps {
      sh ''' 
      sudo pm2 delete all
      sudo pm2 start ./bin/www
      echo "hi"
      '''
      }
      }
    
  }


}
