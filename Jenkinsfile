pipeline {
  agent any
  stages {
    stage('Build'){
      steps {
        echo 'Running build!!!!!'
      }
    }
    stage('Two'){
      steps {
        input('Do you want to proceed?')
      }
    }
    stage('Three'){
    when {
      not {
        branch "master"
      }
    }
    steps {echo "ths is not the master branch"}
    }
    stage('Four'){
      parallel {
        stage('Unit Test'){
          steps {echo "Running the unit test"}
        }
        stage('Integration Test'){
          agent {
            docker {
              reuseNode true
              image 'ubuntu'
            }
          }
          steps {echo "Running the integration test"}
        }
      }
    }
  }
}
