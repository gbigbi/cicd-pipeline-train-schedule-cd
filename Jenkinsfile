pipeline{
	agent any
	options {
		buildDiscarder logRotator(artifactDaysToKeepStr: '', 
		artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
		}

	stages{
		stage("Checkout"){
			steps{
				checkout scmGit(
					branches: [[name: "*/master"]],
					userRemoteConfigs: [[
						url:"https://github.com/gbigbi/cicd-pipeline-train-schedule-cd.git"
					]]
				)
			}
		}
		stage("Build with gradle"){
			steps{
				echo "Running build automation"
				sh './gradlew build --no-daemon'
			}
		}
		stage("Test build "){
			steps{
				 sh './gradlew test'
			}
		}
		stage("Archive a build"){
			steps{
				archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
			}
		}
	}
}
