pipeline {
	agent {docker { image 'maven:3.8.1'} }
	stages{
		stage('Build') {
				steps{
					echo "Build"
				}
			}
		stage('Test') {
				steps{
					echo "Test"
				}
			}
		stage('Integration Test') {
				steps{
					echo "Integration Test"
				}
			}	
	}
	post{
		always{
			echo "Always Run"
		}
		success{
			echo "Success"
		}
		failure{
			echo "Failure"
		}
	}

}
