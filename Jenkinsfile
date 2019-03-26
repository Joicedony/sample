pipeline{
	agent any
	environment {
		sample = credentials('sample')
	}
	stages{
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Attach'){
			steps{
				sh 'mvn clean package -DattachMuleSources'
			}
		}
		stage('Test'){
			steps{
				sh 'mvn clean package test -Dmunit.test=*.*'
			}
		}
		stage('Deploy'){
			steps{
				sh 'mvn clean package deploy -DmuleDeploy'
			}
		}
	}
}