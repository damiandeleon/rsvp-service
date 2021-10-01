pipeline {
    agent any

    stages {

        stage('build') {
            steps {
              sh '''
                 ./mvnw -DskipTests clean compile
              '''
            }
        }

        stage('test') {
            steps {
              sh '''
                         sh "chmod +x -R ${env.WORKSPACE}"
                         sh './jenkins/test.sh'
              '''
            }
        }

        stage('deliver') {
            steps {
              echo 'Deploying...'
              sh '''
                 git push https://git.heroku.com/rsvp-service-damian-deleon.git HEAD:main -f
              '''
            }
        }

    }
}
