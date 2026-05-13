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
           allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure'],[path: 'C:/repo/jenkins-2025-12/out/smoke/allure']]
           junit 'out/syntax-check/junit/junit.xml'           
           junit 'C:/repo/jenkins-2025-12/out/smoke/*.xml'
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
                        bat "chcp 65001\n vrunner xunit" 
                    }
                    catch (Exception Exc) {
                        currentBuild.result = 'UNSTABLE'    
                    }
                }
            }
        }
        stage("Vanessa") {
            steps {
                 script {
                    try {
                        bat "chcp 65001\n vrunner vanessa" 
                    }
                    catch (Exception Exc) {
                        currentBuild.result = 'UNSTABLE'    
                    }
                }
            }
        }
    }
}
