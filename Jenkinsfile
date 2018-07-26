pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        ant -f build.xml -v
      }
    }
  }
}
