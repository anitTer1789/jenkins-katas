pipeline {
  agent any
  stages {
    stage('Build app') {
      parallel {
        stage('Build app') {
          agent {
            docker {
              image 'gradle:6-jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
          }
        }

        stage('Say hello') {
          steps {
            sh 'echo "Hello world"'
          }
        }

      }
    }

  }
}