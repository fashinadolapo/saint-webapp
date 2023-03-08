pipeline {
   agent any

   environment {
     // You must set the following environment variables
     // dolapofashina@gmail.com
     // dolapofashina (it doesn't matter if you don't have one)
     
     SERVICE_NAME = "fleetman-webapp"
     REPOSITORY_TAG="${dolapofashina}/${dolapofashina@gmail.com}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
      stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${dolapofashina}/${SERVICE_NAME}"
         }
      }
      stage('Build') {
         steps {
            sh 'echo No build required for Webapp.'
         }
      }

      stage('Build and Push Image') {
         steps {
           sh 'docker image build -t ${REPOSITORY_TAG} .'
         }
      }

      stage('Deploy to Cluster') {
          steps {
            sh 'envsubst < ${WORKSPACE}/deploy.yaml | kubectl apply -f -'
          }
      }
   }
}
