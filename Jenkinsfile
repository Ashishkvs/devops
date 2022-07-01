pipeline {
    agent any

    stages {
         stage('Git Checkout') {
            steps {
                echo 'Fetching Git Repo $GIT_BRANCH'
                git 'https://github.com/Ashishkvs/Juint-test-case'
            }
        }
        stage('Build') {
            steps {
                echo 'Build java Application'
            }
        }
         stage('Test') {
            steps {
                echo 'Testing Junit'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
