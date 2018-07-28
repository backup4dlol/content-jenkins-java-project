pipeline {
  agent none
  stages {
        stage('Unit Tests') {
            agent {
              label 'slave'
                }
              steps {
                sh 'ant -f test.xml -v'
                junit 'reports/result.xml'
      }
    }
    stage('build') {
                  agent {
                    label 'slave'
                    }
      steps {
        sh 'ant -f build.xml -v'
      }
      post {
        success {
          archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
        }
       }
    }
     stage('deploy') {
            agent {
              label 'slave'
                }
       steps {
          sh "cp dist/rectangle*.jar /var/www/html/rectangles/all/dlolrectangle.jar"
         }
       }
        stage("Running on CentOS") {
      agent {
        label 'slave'
      }
      steps {
        sh "wget http://192.168.56.112/rectangles/all/dlolrectangle.jar"
        sh "java -jar dlolrectangle.jar 3 4"
      }
    }
    stage("Test on Debian") {
      agent {
        docker 'openjdk:8u171-jre'
      }
      steps {
        sh "wget http://192.168.56.112/rectangles/all/dlolrectangle.jar"
        sh "java -jar dlolrectangle.jar 3 4"
      }
     }
    stage('Promote to Green') {  
            agent {
             label 'slave'
                }
     steps {
      sh "cp /var/www/html/rectangles/all/dlolrectangle.jar /var/www/html/rectangles/green/dlolrectangle.jar"
       }
      }
     }
}
