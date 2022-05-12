@Library('shared-build-agents@main') _
podTemplate(yaml: readTrusted('podTemplates/golang-maven.yaml')) {
  node(POD_LABEL) {
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
