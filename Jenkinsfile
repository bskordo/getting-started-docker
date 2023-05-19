pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        sh """
          which docker
        """
      }
    }
    stage("run") {
      steps {
        sh """
          docker run --rm hello_there
        """
      }
    }
    stage("show") {
      steps {
        sh """
          docker images
        """
      }
    }
  }
}
