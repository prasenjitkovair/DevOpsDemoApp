pipeline
{
	agent any
	stages
	{
		stage('build')
		{
			steps
			{
				git 'https://github.com/prasenjitkovair/DevOpsDemoApp.git'
				
				script {
                    def mvn_version = 'maven_3_5_4'
					withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
					  sh "mvn clean install"
					}
                }
				
				sh "echo ${JOB_NAME}"
			}
			
			post
			{ 
				success { 
					echo 'Archiving the Artifact..'
					archiveArtifacts artifacts: 'target/*.war'
				}
			}
			
		}
		
		stage('test')
		{
			steps
			{
				echo 'testing..'
			}
		}
	}
	
}
