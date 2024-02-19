pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install htmlhint-cli'
            }
        }
        stage('Test') {
            steps {
                script {
                    def desiredUser = "ManasDe2"  
                    def latestCommit = sh(script: "curl -s https://api.github.com/repos/ManasDe2/devops5/commits | jq -r '.[0].author.login'", returnStdout: true).trim()

                    if (latestCommit == desiredUser) {
                        currentBuild.result == 'SUCCESS'
                        echo "Latest commit is authored by ${desiredUser}"
                        
                    } else {
                        error "Latest commit is not authored by ${desiredUser}"
                        currentBuild.result == 'FAILURE'
                    }
                }
            }
        }
        stage('Deployment') {
            steps {
                sh 'sudo chmod 777 -R ./*.html'
                sh 'sudo -S cp -r ./*.html /var/www/html/'
                sh 'sudo systemctl restart nginx'
            }
        }
    }
    
    post {
        success {
            // Actions to perform when the pipeline succeeds
            echo 'Pipeline succeeded!'
        }
        failure {
            // Actions to perform when the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
