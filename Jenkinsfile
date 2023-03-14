pipeline {
agent any
  stages {
    stage ('ssh'){
      steps {
        sshagent(credentials : ['pem-file']) {
        sh '''
            [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0700 ~/.ssh
            ssh-keyscan -t rsa,dsa 10.0.2.153 >> ~/.ssh/known_hosts
            ssh ec2-user@10.0.2.153
        '''
      }
    }
    }
/*
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
  */  
  }


}
