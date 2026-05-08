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
           bat "echo always"
        }

        failure {
            bat "echo failure"
        }

        success {
            bat "echo succes"
        }

    }

    stages {      
        stage("Build test base") {
            steps {                
                bat "chcp 65001\n vrunner init-dev --v8version 8.3.23.1912 --dt C:\\jenkins\\template\\1Cv8.dt  --src .\\src\\cf"
                //bat "echo Hello, we are learning jenkins"
            }
        }
    }
}
