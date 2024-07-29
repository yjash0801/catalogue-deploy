pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    // environment {
    //     packageVersion = ''
    //     nexusURL = '172.31.38.156:8081'
    // }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is the environment?')
    }
    // build
    stages {
        stage('Print version') {
            steps {
                sh '''
                echo "version: ${params.version}"
                echo "environment: ${params.environment}"
                '''
            }
        }
    }
    // post build
    post {
        always {
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure {
            echo 'This runs when pipeline is failed, used to send some alerts'
        }
        success {
            echo 'This runs when pipeline is success'
        }
    }
}
