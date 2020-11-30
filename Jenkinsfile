pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build'
        SWEAGLEUpload(actionName: 'uploadSettings', fileLocation: 'settings.properties', format: 'properties', nodePath: 'Apollo,Components,Files', filenameNodes: true, tag: '${BUILD_ID}')
      }
    }

    stage('Test') {
      steps {
        echo 'Test'
        SWEAGLEValidate(actionName: 'ValidateConfig', mdsName: 'Icarus', noPending: true, showResults: true, stored: true)
      }
    }

    stage('deploy PROD') {
               when {
                  branch 'master'
               }
                steps{
                  snDevOpsStep ()
                   echo "deploy in prod"
                  snDevOpsChange()              
                }
            }
  }
}
