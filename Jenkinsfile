pipeline {
    agent any

    environment {
        NAME = 'BONFY'
    }

    stages {
        stage('Step 1') {
            steps {
                echo 'Hello Step 1'
                echo 'Hello ${NAME}'
            }
        }

        stage('Step 2') {
            steps {
                NAME = 'Jane'
                echo 'Hello Step 2'
                echo 'Hello ${NAME}'
            }
        }
    }

     post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}