pipeline {
  agent any

  stages {
    stage('build') {
    agent {docker { image 'jenkinsci/slave:latest'} }
      steps {
        sh 'javac -d . src/*.java'
        sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
        sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
            }
                    }
    stage('run') {
    agent {docker { image 'node:7-alpine'} }
      steps {
        sh 'java -jar rectangle.jar 7 9'
            }
                }
        }
  post {
    success {
      sh 'echo SUCCESS'
            }
       }
}
