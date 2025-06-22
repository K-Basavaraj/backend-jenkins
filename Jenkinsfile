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
     //appversion = '' //this is global varible we can use any where inthe pipeline
    }
   stages {
     stage('debug') {
            steps {
                echo 'debugging..'
                sh 'env'
            }
     }
      stage('read the version') {
        steps {
          script {
            def packageJson = readJSON file: 'package.json'
            // appversion = packageJson.version
            // echo "App version: ${appversion}"
            env.appversion = packageJson.version
            echo "App version: ${env.appversion}"
          }
       }
    }
    stage('install dependencies'){
        steps {
            sh 'npm install'
        }
    }
    stage('Docker build'){
        steps {
            sh """
              docker build -t basavaraj0509/backend:${appversion} .
              docker images
            """
        }
    }
  }
}