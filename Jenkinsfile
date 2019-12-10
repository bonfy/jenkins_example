pipeline {
    agent any

    options
	{
		skipDefaultCheckout()
		buildDiscarder(logRotator(numToKeepStr: '20'))
		timestamps()
	}

    // environment {
    //     NAME = 'BONFY'
    // }

    def PWD = pwd()

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('Step 1') {
            steps {
                echo 'Hello Step 1'

                echo "Current folder: ${PWD}"
                // echo "Hello ${NAME}"

                script
				{
                    env.NAME = "BOB"
                    env.Title = "title"
                }

                echo "After set env: Hello ${NAME}"
                echo "Title: ${Title}"
            }
        }

        stage('Step 2') {
            steps {
                echo 'Hello Step 2'
                echo "Hello ${NAME}"
                echo "Title: ${Title}"
                echo "Hello ${params.PERSON}"
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