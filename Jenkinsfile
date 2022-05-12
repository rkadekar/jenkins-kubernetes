@Library('shared-build-agents@main') _

pipeline {
  agent {
    kubernetes {
      //label "Jenkins-${env.JOB_NAME}"
      yaml libraryResource('podTemplates/golang-maven.yaml')
    }
  }
  stages {
    stage('Get a Maven project') {
      git 'https://github.com/jenkinsci/kubernetes-plugin.git'
      container('maven') {
        stage('Build a Maven project') {
          sh 'mvn -B -ntp clean install'
        }
      }
    }
  }
}
