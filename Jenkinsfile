pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'gradle clean build --refresh-dependencies --info'
            }
        }
        stage('Publish') {
            steps {
                sh 'gradle artifactoryPublish'
            }
        }
    }

    post {
        success {
            echo 'Build success'
            script {
                // Set expire_in value (in minutes)
                def expireInMinutes = 1 // Expire artifacts after 1 minute

                // Define the location of your artifacts
                def artifactDir = 'http://artifactory:8081/artifactory' // Adjust this to your actual artifact path
            }
        }
        failure {
            echo 'Build Failed!!'
        }
    }
}
