pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build'
      }
    }

    stage('Test') {
      steps {
        echo 'Test'
        SWEAGLEValidate(actionName: 'ValidateConfig', mdsName: 'Icarus', noPending: true, showResults: true, stored: true)
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy'
      }
    }

  }
}