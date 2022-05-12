@Library('shared-build-agents@main') _

pipeline {
  agent {
    kubernetes {
      yaml libraryResource('podTemplates/golang-maven.yaml')
    }
  }
  stages {
    stage ('checkout scm') {
        steps {
            // Please avoid committing your test changes to this repository
            git branch: 'master', url: "https://github.com/kubesphere/devops-maven-sample.git"
        }
    }
    stage ('unit test') {
        steps {
            container ('maven') {
                sh 'mvn clean test'
            }
        }
    }
  }
}
