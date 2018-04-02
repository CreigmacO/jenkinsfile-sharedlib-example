pipeline {
  agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
        ansiColor('xterm')
    }

    environment {
         BUILD_ID = "${BUILD_NUMBER}"

    }

    stages {
        stage('Build') {

                      steps {
                          sh 'which docker'
                          sendNothifactions 'STARTED'

                          }
                       }
        stage('TEST'){
            steps{
                sh 'pwd'
               }
          post {
             success {
               // publish html
                publishHTML target: [
                  allowMissing: false,
                  alwaysLinkToLastBuild: false,
                  keepAll: true,
                  reportDir: 'coverage',
                  reportFiles: 'index.html',
                  reportName: 'SafeC Report'
                ]
            }
         }
     }

    post {
        always {
            sendNotifications currentBuild.result
            }
        }

}
