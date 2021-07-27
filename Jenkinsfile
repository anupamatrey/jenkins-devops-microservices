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
		stage('Checkout') {
				steps{
					sh 'mvn --version'
					sh 'docker --version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
				}
			}
		stage('Compile') {
				steps{
					echo "---------------------- Code Compile ------------------------------"
					sh ' mvn clean compile'
				}
			}
		stage('Test') {
				steps{
					echo "---------------------- Test Execution------------------------------"
					sh 'mvn test'
				}
			}
		stage('Integration Test') {
				steps{
					echo "---------------------- Integration Test Execution------------------------------"
					sh 'mvn failsafe:integration-test failsafe:verify'
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
