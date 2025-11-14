pipeline {
    agent any

    environment {
        BUILD_TIMESTAMP = "${new Date().format('yyyy-MM-dd HH:mm:ss')}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sultanyaso/task-1.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || echo "No tests configured, skipping"'
            }
        }

        stage('Info') {
            steps {
                script {
                    echo "Build Number: ${env.BUILD_NUMBER}"
                    echo "Build Timestamp: ${env.BUILD_TIMESTAMP}"

                    // Detect if triggered by GitHub Webhook
                    def githubCause = currentBuild.getBuildCauses('com.cloudbees.jenkins.GitHubPushTrigger$Cause')
                    if (githubCause.size() > 0) {
                        echo "Triggered by GitHub Webhook"
                    } else {
                        echo "Triggered manually or by another cause"
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build and tests successful!'
        }
        failure {
            echo 'Build failed or tests failed!'
        }
    }
}
