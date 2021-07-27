pipeline {
	agent any
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages{
		stage('Permission'){
			steps{
				sh 'chmod 777 *'
			}

		}
		stage('Build') {
				steps{
					sh 'mvn --version'
					sh 'docker --version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
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
