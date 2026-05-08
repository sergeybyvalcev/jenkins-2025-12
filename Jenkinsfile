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
           allure commandline: 'allure', includeProperties: false, jdk: '', resultPolicy: 'LEAVE_AS_IS', results: [[path: 'out/syntax-check/allure']]
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
        stage("Syntax check"){
            step {
                bat "chcp 65001\n vrunner syntax-check"
            }
        }
    }
}
