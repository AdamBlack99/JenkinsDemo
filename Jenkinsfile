pipeline {
    agent{
        label 'slave'
    }
    parameters {
        string(defaultValue: "demo", description: "This will be the title of the html file", name: "TITLE")
        booleanParam(defaultValue: false, description: "Run tests after build",  name: "IF_TEST")
    }
    stages {
        stage('Build') {
            steps{
                script{
                    sh "echo STAGE : BUILD"
                    sh "chmod 777 ./builder.sh"
                    sh "./builder.sh ${params.TITLE}"
                }
            }
            
            
        }
        stage('Test') {
            steps{
                script{
                    sh "echo STAGE : TESTS"
                    if(params.IF_TEST) {
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
            steps{
                script{
                    sh "echo STAGE : RELEASE"
                    sh "mv build_file ${params.TITLE}_${env.BUILDN_UMBER}.html"
                    sh "echo SUCCESS"
                }
            }
        }
    }
}