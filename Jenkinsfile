pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh 'gradle clean build --refresh-dependencies --info'
            }
        }
        stage('publish') {
            steps {
                sh 'gradle artifactoryPublish'
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
