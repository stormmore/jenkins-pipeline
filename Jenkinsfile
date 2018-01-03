def nexus_server = Artifactory.newServer url: https://nexus.mobileservices.razerzone.com/repository/,

pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        any
      }
      steps{
          stage('checkout') {
            echo 'checkout repo'
          }
          stage('test') {
            echo 'maven test'
          }
          stage('package') {
            echo 'maven package'
          }
          stage('verify') {
            echo 'maven verify'
          }
        }
      }
    }
  }
}
