pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './gradlew clean build'
      }
    }

    stage('DockerPublish'){
        def poc_dcos = docker.build "aayushjain/playground:${env.GIT_COMMIT}"
        poc_dcos.push()
    }
  }
}