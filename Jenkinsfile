pipeline {
  agent {
    label 'slave'
    }
  stages {
        stage('Unit Tests') {
              steps {
                sh 'ant -f test.xml -v'
                junit 'reports/result.xml'
      }
    }
    stage('build') {
      steps {
        sh 'ant -f build.xml -v'
      }
    }
     stage('deploy') {
       steps {
          sh "cp dist/rectangle*.jar /var/www/html/rectangles/all/"
         }
       }
  }
}
