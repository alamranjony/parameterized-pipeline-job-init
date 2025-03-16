pipeline {
  agent any
  stages {
    stage('Echo Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'mvn -version'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTests=true'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Unit Test') {
      steps {
        script {
          sh "mvn test"
        }

        junit 'target/surefire-reports/TEST-*.xml'
      }
    }

  }
  tools {
    maven 'M398'
  }
}