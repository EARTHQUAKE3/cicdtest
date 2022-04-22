pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/EARTHQUAKE3/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t qkrtjswo03/testweb:newnewmain .
        sudo docker push qkrtjswo03/testweb:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
	sudo kauth
        sudo kubectl set image deployment deploy-main ctn-main=qkrtjswo03/testweb:newnewmain
        '''
      }
    }
  }
}
