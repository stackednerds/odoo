pipeline {
    agent any

    environment {
        APP_NAME = "odootest"
        RELEASE = "1.0.0"
        DOCKER_USER = ""
        DOCKER_PASS = ''
        IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
        IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
        SCANNER_HOME=tool 'sonar-scanner' 
    }
    stages {
        stage("Sonarqube Analysis") {
            steps {
                script {
                    withSonarQubeEnv('sonar-scanner') {
                        sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=odootest \
                    -Dsonar.projectKey=odootest '''
                    }
                }
            }

        }
        
    }
   
}
