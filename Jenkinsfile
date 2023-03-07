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
      pm2 delete all
      pm2 start bin/www
      '''
      }
      }
    
  }


}
