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

pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        echo 'testing nexus_server'
        script {
          def nexus_server = Artifactory.newServer url: MAVEN_URL,
                                                   credentialsId: MAVEN_CREDENTIALSID
          def rtMaven = Artifactory.newMavenBuild()

          echo MAVEN_URL,  MAVEN_CREDENTIALSID
        }
      }
    }
  }
}
