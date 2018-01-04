/*
TO-DO:
  - deterministic method to perform a build; to allow for redeployments of
    previous builds without rebuilding
*/

def nexus_server = Artifactory.newServer url: 'https://nexus.mobileservices.razerzone.com/repository/',
                                         credentialsId: 'nexus-maven'
def rtMaven = nexus_server.newMavenBuild()
def buildInfo

pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        sh "echo 'checkout repo'"
        sh "echo 'maven test'"
        sh "echo 'maven package'"
        sh "echo 'maven verify'"
      }
    }
  }
}
