pipeline {
    agent any
    tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
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
                sh 'mvn install'
            }
        }
        
        stage ('Scantist') {
            steps {
                sh '''
                    #!/bin/bash
                    export SCANTIST_IMPORT_URL=https://api.scantist.io/ci-scan/
                    export SCANTISTTOKEN=$your_copied_access_token

                    bash <(curl -s https://scripts.scantist.com/ci-jenkins.sh)
                '''
            }
        }
    }
}
