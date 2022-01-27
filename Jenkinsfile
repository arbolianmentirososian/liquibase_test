pipeline {
    agent any
    environment {
        GIT_EMAIL = sh(script: "git show -s --format='%ae' HEAD | tr -d '\n'", returnStdout: true)
    }
    options {
	    buildDiscarder(logRotator(artifactNumToKeepStr: '7'))
	}
    stages {
        stage('Validate') {
            steps {
                withEnv(['PATH_LB_VALIDATOR=/var/jenkins_home/bin']) {
                    sh '''
                    $PATH_LB_VALIDATOR/liquibase_validator
                    '''
                }
            }
        }
    }
}