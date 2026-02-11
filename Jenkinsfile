pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
     environment {
        COURSE = "Jenkins"
        appVersion = ""
    }
    options {
        timeout(time: 10, unit: 'MINUTES') 
        disableConcurrentBuilds()
    }
    stages {
        stage('Read Version') {
            steps {
                script {
                    def packageJSON = readJSON file: 'package.json'
                    appVersion = packageJSON.Version
                    echo "app version: ${appVersion}"

                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh '''
                        echo "Testing"
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh '''
                        echo "Deploying"
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success {
            echo 'success'
        }
        failure {
            echo 'failure'
        }
        aborted {
            echo 'pipeline is aborted'
        }
    }
}
