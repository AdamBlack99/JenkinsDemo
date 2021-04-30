pipeline {
    agent{

    }
    parameters {
        string(defaultValue: "demo", description: "This will be the title of the html file", name: "TITLE")
        booleanParam(defaultValue: false, description: "Run tests after build",  name: "IF_TEST")
    }
    stages {
        stage('Build') {
            step{
                script{
                    sh "echo STAGE : BUILD"
                    sh "./builder.sh ${params.TITLE}"
                }
            }
            
            
        }
        stage('Test') {
            step{
                script{
                    sh "echo STAGE : TESTS"
                    if(${IF_TEST}) {
                        sh "echo simulating tests.."
                        sh "sleep 5"
                        sh "echo SUCCESS"
                    } else {
                        sh "echo Tests skipped"
                    }
                }
            }

        }
        stage('Release') {
            step{
                script{
                    sh "echo STAGE : RELEASE"
                    sh "mv build_file ${params.TITLE}_${env.BUILD_NUMBER}"
                    sh "${params.TITLE}_${env.BUILD_NUMBER} released"
                    sh "echo SUCCESS"
                }
            }
        }
    }
}