pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/bskordo/getting-started-docker.git'
            }
        }
        
        stage('Create Tag and Branch') {
            steps {
                script {
                    def commitHash = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                    def branchName = 'new-branch'
                    
                    sh "git tag -a tag-${commitHash} -m 'Tagging commit ${commitHash}'"
                    sh 'git push --tags'
                    
                    sh "git checkout -b ${branchName}"
                    sh "git push origin ${branchName}"
                }
            }
        }
    }
}
