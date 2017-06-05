pipeline {

  agent any
  stages {

    stage('Build') {
      steps {
        sh './gradlew clean build'
        sh 'git rev-parse HEAD > commit'
        def commit = readFile('commit').trim()
        script {
        docker.withRegistry('https://registry.hub.docker.com', '1b897fc4-3a7c-419d-b0c8-9695c9d96590') {
                       def app = docker.build("aayushjain/playground")
                      app.push("${commit}")
                      app.push("latest")
                  }

        }
      }
    }
  }
}