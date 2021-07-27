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
					//sh 'mvn test'
				}
			}
		stage('Integration Test') {
				steps{
					echo "---------------------- Integration Test Execution------------------------------"
					//sh 'mvn failsafe:integration-test failsafe:verify'
				}
			}
		stage('Package') {
				steps{
					echo "---------------------- Building a Package-----------------------------"
					sh 'mvn package -DskipTests'
				}
			}	
		stage('Build Docker Image'){
				steps{
					echo "---------------------- Build a Docker Image------------------------------"
					 //"docker build - t anupamattrey/currency-exchange-devops:$env.BUILD_TAG"	
					 script{
						 dockerImage = docker.build("anupamattrey/currency-exchange-devops:${env.BUILD_TAG}")
					 }
				}
			}
		stage('Push Docker Image'){
				steps{
					script{
						docker.withRegistry('','Docker_Id'){
						dockerImage.push()
						dockerImage.push('latest')
						}
						
					}

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
