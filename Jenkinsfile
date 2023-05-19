stages {
    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Scanning Image') {
        steps {
            sysdigImageScan engineCredentialsId: 'sysdig-secure-api-credentials', imageName: "hello_there:latest"
        }
    }
}
