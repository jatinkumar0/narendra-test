pipeline {
agent any
  stages {
    stage ('Build'){
      steps {
      sh ''' 
      docker build -t bhupesh-test:v$BUILD_NUMBER .
      '''
      }
      }
    
      stage ('Deploy'){
      steps {
      sh ''' 
      docker stop bhupesh-test
      docker rm bhupesh-test
      docker run -itd -p 3000:3000 --name bhupesh-test bhupesh-test:v$BUILD_NUMBER
      '''
      }
      }
    
  }


}
