/*
TO-DO:
  - deterministic method to perform a build; to allow for redeployments of
    previous builds without rebuilding
*/

// Source repository
def GIT_REPO = 'https://github.com/stormmore/jenkins-pipeline.git'
def GIT_DEV_BRANCH = 'master'

// Maven repository
def MAVEN_URL = 'https://nexus.mobileservices.razerzone.com/repository/'
def MAVEN_CREDENTIALSID = 'nexus-maven'
def MAVEN_RELEASES = 'maven-releases'
def MAVEN_SNAPSHOTS = 'maven-snapshots'

pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        script {
          def server = Artifactory.newServer(url: 'https://nexus.mobileservices.razerzone.com/repository/', credentialsId: "nexus-maven")
        }
      }
    }
  }
}
