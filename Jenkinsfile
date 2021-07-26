pipeline {
	agent any
	environment{
		dockerHome = tool 'MyDocker'
		mavenHome = tool 'MyMaven'
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
