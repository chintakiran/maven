pipeline
{
    agent any
    stages
    {
        stage('Continuos Download')
        {
            steps
	    {

                        git 'https://github.com/chintakiran/maven.git'
            }
        }
         stage('Continuos Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
         stage('Continuos Deployment')
        {
            steps
            {
              sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.27.132:/var/lib/tomcat9/webapps/testapp.war'
        }
	}
        stage('Continuos Testing')
        {
            steps
            {
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'  
              sh '''java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'''
            }
        }
         stage('Continuos Delivery')
        {
            steps
            {
               sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.25.75:/var/lib/tomcat9/webapps/prodapp.war'
            
            }
        }
        
        
    }
}
