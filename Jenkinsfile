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
                        //sh "git config user.name ${env.GIT_USERNAME}"
                        //sh "git config user.email samat.study@gmail.com"
                        def commitHash = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                        def branchName = 'new-branch'
                        sh " echo $GIT_USERNAME"
                        sh "git checkout  ${branchName}"
                        sh "git push https://${env.GIT_USERNAME}:${env.GIT_PASSWORD}@github.com/bskordo/getting-started-docker.git new-branch"
                
                    }
                }
            }
        }
        stage('Create Tag and Branch') {
            steps {
                script {
                    def commitHash = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                    def branchName = 'new-branch'
                    //sh "echo $GIT_USERNAME"
        
                   // sh 'git push --tags'
                    
                    //sh "git checkout -b ${branchName}"
                    //sh "git push https://${env.GIT_USERNAME}:${env.GIT_PASSWORD}@github.com/bskordo/getting-started-docker.git new-branch"
                    //sh "git push origin ${branchName}"
                }
            }
        }
    }
}
