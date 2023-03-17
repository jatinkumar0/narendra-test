pipeline {
agent any
  stages {
/*
    stage ('ssh'){
      steps {
        sshagent(credentials : ['pem-file']) {
        sh '''
            [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0700 ~/.ssh
            ssh-keyscan -t rsa,dsa 13.210.58.98 >> ~/.ssh/known_hosts
            ssh ec2-user@13.210.58.98 sudo yum install httpd -y
            ssh ec2-user@13.210.58.98 sudo systemctl start httpd
            ssh ec2-user@13.210.58.98 sudo systemctl status httpd
        '''
      }
    }
    }
 */
    
    stage ('Test Dockerfile'){
      steps{
      sh '''
      sudo npm install -g dockerlint
      sudo dockerlint Dockerfile
      '''
      }
    }
    stage ('Build'){
      steps {
      sh ''' 
      sudo docker build -t bhupesh-test:v$BUILD_NUMBER .
      '''
      }
      }
    stage ('Scan Docker Image'){
      steps{
      sh '''
      sudo yum install docker-scan-plugin
      sudo docker scan bhupesh-test:v$BUILD_NUMBER
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
