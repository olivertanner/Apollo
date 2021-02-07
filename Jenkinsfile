pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build'
        snDevOpsStep(enabled:true,ignoreErrors:false)
        SWEAGLEUpload(actionName: 'uploadSettings', fileLocation: 'settings.properties', format: 'properties', nodePath: 'Apollo,Components,Files', filenameNodes: true, tag: '${BUILD_ID}')
      }
    }

    stage('Test') {
      steps {
        echo 'Test'
        snDevOpsStep(enabled:true,ignoreErrors:false)
        SWEAGLEValidate(actionName: 'ValidateConfig', mdsName: 'Icarus', noPending: true, showResults: true, stored: true)
      }
    }

    stage('deploy') {
      steps {
        echo 'deploy in prod'
        snDevOpsStep(enabled:true,ignoreErrors:true)
        snDevOpsChange()
      }
    }

  }
}
