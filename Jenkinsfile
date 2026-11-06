
pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/esurendrababu/my-static-site.git'
        BRANCH_NAME = 'master'
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning source from GitHub..."

                git branch: env.BRANCH_NAME,
                    url: env.REPO_URL
            }
        }

        stage('Verify Files') {
            steps {
                echo "Validating static assets..."

                sh '''
                    echo "Checking project files..."
                    ls -la

                    if [ ! -f index.html ]; then
                        echo "Error: index.html not found!"
                        exit 1
                    fi

                    echo "Validation successful!"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "Assets verified. Ready for deployment."
            }
        }
    }

    post {
        success {
            echo "CI/CD Pipeline completed successfully!"
        }

        failure {
            echo "CI/CD Pipeline failed!"
        }

        always {
            cleanWs()
        }
    }
}
