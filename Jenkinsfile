pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
			    checkout scm
			}
		}

		stage('OWASP DependencyCheck') {
					tools {
                   		jdk "jdk-11"
                	}
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml --disableYarnAudit --disableNodeAudit', odcInstallation: 'Default'
			}
		}
	}
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}