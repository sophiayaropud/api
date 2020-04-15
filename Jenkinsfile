pipeline {
   agent { 
       label 'linux'
   }
   stages {
      stage('run docker') {
         steps {
            script{
                sh 'sudo docker start 42b4e3e67d45'
            }
         }
      }
      stage('run test'){
          steps{
              script{
                  git 'https://github.com/sophiayaropud/api.git'
                  sh 'mvn -f /home/Sophia_Yaropud/workspace/pipeline/Rest_Demo/pom.xml clean test'
              }
          }
      }
      stage('close docker'){
          steps{
              script{
                sh 'sudo docker stop 42b4e3e67d45'
              }
          }
      }
      stage('allure'){
          steps{
              script{
                  allure includeProperties: false, jdk: '', results: [[path: 'Rest_Demo/target/allure-results']]
              }
          }
      }
   }
}
