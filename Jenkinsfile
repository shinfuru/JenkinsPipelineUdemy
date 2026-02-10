pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub webhook'
            }
        }
        stage('Build') {
            steps {
                echo 'Build World'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy World'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html S3://test-env-jenkins-udemy-shintaro')
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Test World'
            }
        }
        stage('Release') {
            steps {
                echo 'Release World'
            }
        }
    }
}
