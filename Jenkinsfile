pipeline {
  agent {
    docker {
      image 'nginx'
      args '/bin/bash'
    }

  }
  stages {
    stage('check') {
      steps {
        sh '''pwd
ls -l
echo "now is chkec..."'''
      }
    }

    stage('test') {
      steps {
        echo 'this is test ...'
        timeout(time: 10, activity: true) {
          retry(count: 10) {
            sleep 2
            archiveArtifacts(artifacts: '*.jar', allowEmptyArchive: true)
          }

        }

      }
    }

    stage('delopy') {
      steps {
        echo 'delopy'
      }
    }

  }
  environment {
    name = 'kai'
    age = '12'
  }
}