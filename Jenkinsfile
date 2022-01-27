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
                script {
                    sh """
                        liquibase_validator
                    """
                }
            }
        }
    }
}