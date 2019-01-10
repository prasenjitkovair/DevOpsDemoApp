pipeline
{
	agent any
	stages
	{
		stage('build')
		{
			steps
			{
				git 'https://github.com/prasenjitkovair/JenkinsDemo.git'
				
				script {
                    def mvn_version = 'maven_3_5_4'
					withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
					  sh "mvn -f KovairTraining/pom.xml compile"
					}
                }
				
			}
			
			post
			{ 
				success { 
					echo 'Archiving the Artifact..'
					archiveArtifacts artifacts: 'KovairTraining/target/*.jar'
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
