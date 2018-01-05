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

    // Slack
    SLACK_TEAM = 'razersf'
    SLACK_BUILD_TOKEN = 'eKXxnFcBwFsYryVOpjylNorV'
    SLACK_BUILD_CHANNEL = '@graham.burgess'
    SLACK_DEPLOY_TOKEN = 'eKXxnFcBwFsYryVOpjylNorV'
    SLACK_DEPLOY_CHANNEL = '@graham.burgess'
  }

  stages {
    stage('Build Preparation') {
      when {
        branch 'master'
      }
      agent any
      steps {
        parallel(
          'notify': {
            slackSend teamDomain: SLACK_TEAM, token: SLACK_BUILD_TOKEN,
                      message:  "BUILD STARTED: Job '${env.JOB_NAME}  [${env.BUILD_NUMBER}]' (<${env.RUN_DISPLAY_URL}|Open>)",
                      channel: SLACK_BUILD_CHANNEL, color: '#0000FF'

          },
          'stash': {
            stash 'source'
          },
          'jave_version': {
            sh 'java -version'
          }
          )
      }
    }

    stage('Build Pretesting') {
      when {
        branch 'master'
      }
      agent any
      steps {
        sh 'mvn clean test'
      }
      post {
        failure {
          slackSend teamDomain: SLACK_TEAM, token: SLACK_BUILD_TOKEN,
                    message:  "BUILD PRETEST FAILED: Job '${env.JOB_NAME}  [${env.BUILD_NUMBER}]' (<${env.RUN_DISPLAY_URL}|Open>)",
                    channel: SLACK_BUILD_CHANNEL, color: '#FF0000'
        }
      }
    }

    stage('Build Packaging') {
      when {
        branch 'master'
      }
      agent any
      steps {
        sh 'mvn clean install -Dmaven.test.skip=true'
      }
      post {
        failure {
          slackSend teamDomain: SLACK_TEAM, token: SLACK_BUILD_TOKEN,
                    message:  "BUILD PRETEST FAILED: Job '${env.JOB_NAME}  [${env.BUILD_NUMBER}]' (<${env.RUN_DISPLAY_URL}|Open>)",
                    channel: SLACK_BUILD_CHANNEL, color: '#FF0000'
        }
      }
    }
  }
}
