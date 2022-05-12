@Library('shared-build-agents@main') _

pipeline {
  agent {
    kubernetes {
      yaml libraryResource('podTemplates/golang-maven.yaml')
    }
  }
  stages {
    stage('Run Maven') {
      steps {
        container('maven') {
          sh 'git clone https://github.com/jenkinsci/kubernetes-plugin.git'
          sh 'mvn -B -ntp clean install'
        }
      }
    }
  }
}
