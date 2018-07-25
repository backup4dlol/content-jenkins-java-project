pipeline {
  agent none

  stages {
    stage('build') {
      steps {
        ant -f build.xml -v
      }
    }
}
}
