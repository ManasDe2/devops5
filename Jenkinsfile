pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from version control (e.g., Git)
                checkout scm 
            }
        }
         stage('Echo File') {
            steps {
                // Echo the content of a file
                script {
                    def fileContent = readFile 'hello.txt'
                    echo "File content: ${fileContent}"
                }
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
