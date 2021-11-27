pipeline {
    agent any
    tools {
        maven 'Maven_3.8.3'
        jdk 'Java_8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn package' 
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
}
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
