pipeline {
	agent none
	stages {
	
		stage('Non-Parellel Stage') {
			agent {
				label "master"
			}
			steps {
					echo "This stage will be executed first";
					
			}
		}
		
		stage('Run Tests') {
			parallel {
				stage('Test on Windows') {
					agent {
						label "Agent2"
					}
					steps {
						echo "Task1 on Agent"
					}
				}
				stage('Test on Master') {
					agent {
						label "master"
					}
					steps {
						echo "Task1 on Master"
					}
				}
			}
			
		}
	}
	
	post {
		always {
			echo 'This will always run'
		}
		success {
			echo 'This will run only if successful'
		}
		failure {
			echo 'This will run only if failed'
		}
		unstable {
			echo 'This will run only if the run was marked as unstable'
		}
		changed {
			echo 'This will run only if the state of the pipeline was changed'
		}
	}
}
