pipeline{
	agent any
	options {
		buildDiscarder logRotator(artifactDaysToKeepStr: '', 
		artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
		}

	stages{
		stage("Build with gradle"){
			steps{
				echo "Running build automation"
				sh './gradlew build --no-daemon'
			}
		}
		stage("Archive a build"){
			steps{
				archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
			}
		}
	}
}
