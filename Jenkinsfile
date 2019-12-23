#!groovy

// Libraries import


// Global Defautls
def project = "Hello"


pipeline {
    agent any


    // Defination

    options
	{
		// skipDefaultCheckout()
		// buildDiscarder(logRotator(numToKeepStr: '20'))
		timestamps()
	}

    // environment {
    //     NAME = 'BONFY'
    // }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('Step 1') {
            steps {

                echo "Project Name: ${project}"

                def PWD = pwd()
                echo "Current folder: ${PWD}"

                throw new Exception("Something went wrong!")

                script
                {
                    dir('utils') 
                    {
                        def cur_fd = pwd()
                        echo "in dir current dir: ${cur_fd}"

                        sh "mkdir -p output"
                        writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."
                    }

                    def fd = pwd()
                    println "out dir current dir: ${fd}"
                }


                echo 'Hello Step 1'

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
            // deleteDir() /* clean up our workspace */
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