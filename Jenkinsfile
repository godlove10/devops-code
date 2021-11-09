pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry = "1983godlove/devops-pipeline"
    registryCredential = 'DockerID'
  } 
  stages {
    stage('Build'){
      steps {
       sh 'mvn clean'
       sh 'mvn install'
       sh 'mvn package'
      }
    }
    stage('Test'){
      steps {
        echo "test step"
        sh 'mvn test'
      }
    }
    stage('Deploy'){
      steps {
        scripts {
        docker.build registry + ":$BUILD_NUMBER"
      }
    }
  }
}
