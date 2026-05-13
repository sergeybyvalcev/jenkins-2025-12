pipeline
{
    agent {
        label '1c-node'
    }

    environment {
        envString = 'world'
    }

    post {
        
        always {            
           allure commandline: 'allure', includeProperties: false, jdk: '', resultPolicy: 'LEAVE_AS_IS', results: [[path: 'out/syntax-check/allure'], [path: 'out/smoke/allure/allure.xml']]
           junit 'out/syntax-check/junit/junit.xml'
        }
        // failure {
        //     // bat "echo failure"
        // }

        // success {
        //     // bat "echo succes"
        // }

    }

    stages {      
        stage("Build test base") {
            steps {                
                bat "chcp 65001\n vrunner init-dev"                
            }
        }
        stage("Syntax check") {
            steps {
                bat "chcp 65001\n vrunner syntax-check"
            }
        }
        stage("Smoke tests") {
            steps {
                 script {
                    try {
                        bat "chcp 65001\n runner xunit" 
                    }
                    catch (Exception Exc) {
                        currentBuild.result = 'UNSTABLE'    
                    }
                }
            }
        }
    }
}
