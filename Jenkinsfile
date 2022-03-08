pipeline{
    agent any
        stages{
            stage('scm'){
                    steps{
                        git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
                    }
                }
            stage('build'){
                    steps{
                        powershell 'mvn clean package'
                    }
                }
            stage('archive'){
	                steps{
                        archiveArtifacts artifacts: 'target/spring-petclinic-2.6.0-SNAPSHOT.jar'
                    }
                }
            stage('postBuild'){
                    steps{ 
                        junit 'target/surefire-reports/*.xml'
                    }
                }
    
            }
}