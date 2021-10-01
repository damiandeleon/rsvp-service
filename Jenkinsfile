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
                 ./mvnw test
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
