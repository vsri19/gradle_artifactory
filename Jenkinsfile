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
                def artifactDir = '/path/to/your/artifacts' // Adjust this to your actual artifact path

                // Cleanup: Remove files older than 1 minute
                sh """
                find ${artifactDir} -type f -mmin +${expireInMinutes} -exec rm -f {} \;
                """
            }
        }
        failure {
            echo 'Build Failed!!'
        }
    }
}
