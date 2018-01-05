/*
TO-DO:
  - deterministic method to perform a build; to allow for redeployments of
    previous builds without rebuilding
*/


pipeline {
  agent none

  environment {
    // Source repository
    GIT_REPO = 'https://github.com/stormmore/jenkins-pipeline.git'
    GIT_DEV_BRANCH = 'master'

    // Maven repository
    MAVEN_URL = 'https://nexus.mobileservices.razerzone.com/repository/'
    MAVEN_CREDSID = 'nexus-maven'
    MAVEN_RELEASES = 'maven-releases'
    MAVEN_SNAPSHOTS = 'maven-snapshots'
  }

  stages {
    stage('build') {
      when {
        branch 'master'
      }
      agent any
      steps {
        stash
      }
    }
  }
}
