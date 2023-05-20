pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/bskordo/getting-started-docker.git'
            }
        }
        stage('Commit and Push') {
            steps {
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'GitUser', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')
                    ]) {
                        // Set the Git credentials
                        sh "git config user.name ${env.GIT_USERNAME}"
                        sh "git config user.email samat.stuyd@gmail.com"
                        
                
                    }
                }
            }
        }
        stage('Create Tag and Branch') {
            steps {
                script {
                    def commitHash = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                    def branchName = 'new-branch'
                    
        
                    sh 'git push --tags'
                    
                    sh "git checkout -b ${branchName}"
                    sh "git push origin ${branchName}"
                }
            }
        }
    }
}
