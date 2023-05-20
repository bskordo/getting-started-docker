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
                        usernamePassword(credentialsId: 'git-credentials', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')
                    ]) {
                        // Set the Git credentials
                        sh "git config user.name ${env.GIT_USERNAME}"
                        sh "git config user.email ${env.GIT_USERNAME}@example.com"
                        
                        // Add the changes to the Git index
                        sh 'git add .'
                        
                        // Commit the changes with a commit message
                        sh 'git commit -m "Commit message"'
                        
                        // Push the changes to the remote repository
                        sh "git push https://${env.GIT_USERNAME}:${env.GIT_PASSWORD}@github.com/your/repository.git master"
                    }
                }
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
