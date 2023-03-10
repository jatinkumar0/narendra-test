pipeline {
agent any
  stages {
    stage ('Build'){
      steps {
      sh ''' 
      sudo docker build -t bhupesh-test:v$BUILD_NUMBER .
      '''
      }
      }
    
      stage ('Deploy'){
      steps {
      sh ''' 
      sudo docker stop bhupesh-test
      sudo docker rm bhupesh-test
      sudo docker run -itd -p 3000:3000 --name bhupesh-test bhupesh-test:v$BUILD_NUMBER
      '''
      }
      }
    
  }


}
