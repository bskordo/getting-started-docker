pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        sh """
          docker verion
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
