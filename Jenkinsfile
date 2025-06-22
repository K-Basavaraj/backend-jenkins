pipeline {
   agent {
     label 'AGENT-1'
   }
   options {
      timeout(time: 5, unit: 'MINUTES')
      disableConcurrentBuilds()
   }
   environment {
     DEBUG = 'true'
     appversion = '' //this is global varible we can use any where inthe pipeline
    }
   stages {
      stage('Version')
        steps {
          script {
            def packageJson = readJSON file: 'package.json'
            appversion = packageJson.version
            echo "App version: ${appversion}"
          }
       }
    }
}