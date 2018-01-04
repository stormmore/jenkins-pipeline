/*
TO-DO:
  - deterministic method to perform a build; to allow for redeployments of
    previous builds without rebuilding
*/

// Source repository
def GIT_REPO = 'https://github.com/stormmore/jenkins-pipeline.git'
def GIT_DEV_BRANCH = 'master'

// Maven repository

pipeline {
  agent none

  environment {
    MAVEN_URL = 'https://nexus.mobileservices.razerzone.com/repository/'
    MAVEN_CREDSID = 'nexus-maven'
    MAVEN_RELEASES = 'maven-releases'
    MAVEN_SNAPSHOTS = 'maven-snapshots'
  }

  stages {
    stage('build') {
      agent any
      steps {
        script {
          def server = Artifactory.newServer url: NEXUS_URL, credentialsId: MAVEN_CREDSID
        }
      }
    }
  }
}
