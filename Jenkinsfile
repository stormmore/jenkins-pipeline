/*
TO-DO:
  - deterministic method to perform a build; to allow for redeployments of
    previous builds without rebuilding
*/
def git_repo = 'https://github.com/stormmore/jenkins-pipeline.git'
def nexus_url = 'https://nexus.mobileservices.razerzone.com/repository/'
def nexus_credentialsId = 'nexus-maven'

pipeline {
  agent none
  stages {
    stage('build') {
      agent any
      steps {
        echo 'testing nexus_server'
        script {
          def nexus_server = Artifactory.newArtifactoryServer url: nexus_url,
                              credentialsId: nexus_credentialsId
          def rtMaven = nexus_server.newMavenBuild()
        }
      }
    }
  }
}
