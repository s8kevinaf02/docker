pipeline {
    agent { label 'SERVER04' }
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: '')
    }
    stages {
        stage('Clone Repository') {
            steps {
                script {
                    //Clone the repository using SSH with private key and checkout the specific branch
                    git credentialsId: 'jenkins-ssh-agents-private-key',
                        url: 'https://github.com/s8kevinaf02/articles-web.git',
                        branch: "${params.BRANCH_NAME}"
                }
            }
        }
        stage('Create a directory') {
            steps {
                script {
                    sh """
                        cd /var/www/html
                        sudo mkdir -p s8kevinaf02/cicd-pipeline/articles || true
                    """ 
                }
            }
        }
        stage('Deploying the Code') {
            steps {
                script {
                    sh """
                        pwd
                        ls -l
                        sudo cp -r * /var/www/html/s8kevinaf02/cicd-pipeline/articles
                    """ 
                }
            }
        }
    }
}