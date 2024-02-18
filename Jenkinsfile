pipeline {
    agent any
    
    stages {
        stage('Echo File') {
            steps {
                // Echo the content of a file
                script {
                    def fileContent = readFile './*.txt'
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
