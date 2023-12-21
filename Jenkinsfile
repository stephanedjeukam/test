pipeline {
	agent any
	tools {
	    maven "Maven3"
	    jdk "JDK8"
	}

	stages {
	    stage('Fetch code') {
            steps {
               git branch: 'main', 
               url: 'https://github.com/stephanedjeukam/test.git'
            }

	    }

	    stage('Build'){
	        steps{
	           sh 'mvn install -DskipTests'
	        }

	        post {
	           success {
	              echo 'Now Archiving it...'
	              archiveArtifacts artifacts: '**/target/*.war'
	           }
	        }
	    }

	    stage('UNIT TEST') {
            steps{
                sh 'mvn test'
            }
        }
	}
}