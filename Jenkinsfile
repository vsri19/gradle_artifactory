pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh 'chmod +x ./gradlew'
                bat './gradlew clean build --refresh-dependencies --info'
            }
        }
        stage('publish') {
            steps {
                bat './gradlew artifactoryPublish'
            }
        }
    }

    post{
        success{
            echo 'Build success'
        }
        failure{
            echo 'Build Failed!!'
        }
    }
}
