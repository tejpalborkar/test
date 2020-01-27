pipeline {
  agent any
  stages {
    stage('compile') {
      steps {
        sh 'sh "mvn clean compile"'
      }
    }

    stage('test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('build') {
      steps {
        sh 'mvn build'
      }
    }

    stage('deploy') {
      steps {
        sh '''sh \'\'\'
docker login -u "tejpalborkar10" -p "tejpal123"
                    docker pull tejpalborkar10/spring-boot-websocket-chat-demo:latest
                    docker stop spring-boot-websocket-chat-demo
                    docker rm spring-boot-websocket-chat-demo
                    docker run -p 9090:9090 --name spring-boot-websocket-chat-demo -t -d tejpalborkar10/spring-boot-websocket-chat-demo:latest
                    docker rmi -f $(docker images -q --filter dangling=true)
                \'\'\''''
      }
    }

  }
}