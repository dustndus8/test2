pipeline {
  agent any
  stages {
    stage(' git clone or git pull' ) {
      steps {
        git url: 'https://github.com/dustndus8/test2.git', branch: 'master'
      }

    }

    stage(' docker image build and push to private-registry') {
      steps {
        sh '''
        docker build -t 192.168.8.100:5000/testweb:blue .
        docker push 192.168.8.100:5000/testweb:blue
        '''
      }
    }

    stage(' deployment, svc creation ' ) {
      steps {
        sh '''
        kubectl apply -f blue.yaml
        '''
      }
    }
  }
}