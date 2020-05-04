pipeline {
   agent any

   stages {
      stage('Hello')
      {
         steps {
            echo 'Hello World'
         }
      }
        stage('Check out from Git')
        {
            steps{
               git credentialsId: 'git_credentials', url: 'https://github.com/Pravina1/web_application'
            }
        }
        stage('Maven build')
        {
            steps{
                    sh 'mvn package'
                 }
        }
        
        stage('upload artifacts on nexus')
        {
            steps{
                    sh 'mvn clean deploy'
                 }
        }
        
        stage('sonar scan')
        {
            steps{
                sh 'mvn sonar:sonar'
            }
        }
        stage('deploy on tomcat')
        {
            steps{
                 sh 'sudo cp target/*.war /var/lib/tomcat8/webapps/'
            }
        }
        
      }
   }

