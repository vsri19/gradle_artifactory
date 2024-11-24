pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh './gradlew clean build --refresh-dependencies --info'
            }
        }
        stage('publish') {
            steps {
                sh './gradlew artifactoryPublish'
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
