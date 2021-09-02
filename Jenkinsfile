pipeline {
  agent any
  stages {
    stage('Clone'){
      agent {
            docker {
              image 'gradle:swarm'
            }

          }
      steps{
        stash name: "code", excludes: "./.git/*"
      }
      
    }
    stage('Build app') {
      options{
        skipDefaultCheckout(true)
      }
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
