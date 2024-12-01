pipeline {
  agent any
  
  tools {
      maven "M399"
  }
  
  stages {
    stage ('Echo Version') {
        steps {
            sh 'echo Print Maven Version'
            sh 'mvn -version'
        }
    }  
    stage('Build') {
      steps {
        //git branch: 'main', url: 'https://github.com/sanjaypsachdev/spring-boot-hello-world.git'
        sh 'mvn clean package -DskipTests=true'
      }
    }
    stage('Unit Test') {
        steps {
            sh 'mvn test'
        }
    }
  }
  post {
    always {
      junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true)
    }
  }
}
