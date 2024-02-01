pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        packageVersion = ''
    }
     options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    // build
    stages {
        stage('Get the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "application version: $packageVersion"
                }
            }
        }
        stage('Install dependencies') {
            steps {
                sh """
                    npm install
                """
            }
        }
         stage('Build') {
            steps {
                sh """
                   ls -la
                   zip -r catalogue.zip ./* -x ".git" -x "*.zip"
                   ls -ltr
                """
            }
        }
        stage('Deploy') {
            steps {
                sh """
                    echo 'Executing from shell script!'
                    #sleep 10
                """
            }
        }
    }
    // post build
    post { 
        always { 
            echo 'I will always get executed irrespective of the pipeline status!'
            deleteDir()
        }
        failure { 
            echo 'This runs when pipeline is failed, used to send some alerts using slack..etc'
        }
        success { 
            echo 'This runs when pipeline executed successfully!'
        }
        aborted { 
            echo 'This runs when pipeline Timeout has been exceeded!'
        }
    }
}