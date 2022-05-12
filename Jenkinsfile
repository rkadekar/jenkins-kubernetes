@Library('shared-build-agents@main') _

pipeline {
  agent {
    kubernetes {
      yaml libraryResource('podTemplates/golang-maven.yaml')
    }
  }
  stages {
    stage('Get a Maven project') {
      steps {
        container('maven') {
          sh 'git clone https://github.com/jenkinsci/kubernetes-plugin.git'
        }
      }
    }
    stage('Run Maven') {
      steps {
        container('maven') {
            sh 'mvn -B -ntp clean install'
        }
      }
    }
  }
}
