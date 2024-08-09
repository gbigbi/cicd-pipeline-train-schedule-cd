pipeline{
	tools {
		jdk 'Java'
		gradle 'gradle'
		maven 'maven'
		}
	agent any
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
				sh 'gradle clean build --no-daemon'
			}
		}
		stage("Test build "){
			steps{
				 sh 'gradle test'
			}
		}
		stage("Archive a build"){
			steps{
				archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true, followSymlinks: false
			}
		}
	}
}
