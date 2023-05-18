pipeline
{
	agent any
	tools
	{
	maven "maven"
	}
        stages {
            stage('Code Checkout'){
			steps{
				git branch: 'main', url: 'https://github.com/Devops9AM/Docker-Web-App.git'

			}
		}
        stage("Unit Test") {
            steps {
                sh 'mvn clean test'
              }
            }
            stage("Code Compile") {
            steps {
                sh 'mvn compile'
              }
            }
        stage("SonarQube analysis") {
            steps {
              withSonarQubeEnv('CodeQuality') {
                sh 'mvn sonar:sonar'
              }
            }
          }
           
        stage(" Building Artifact") {
            steps {
                sh 'mvn clean package'
              
            }
          }
        stage(" Deploy Artifact to Nexus") {
            steps {
                sh 'mvn deploy'
              
            }
          }
          
        }
      }

