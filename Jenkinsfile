pipeline{
    agent any
	/*triggers{
    pollSCM('H * * * 1-5')	
    }*/
    parameters{
      /*  string(name:'MAVENGOAL', defaultValue:'clean package',description:'Enter the maven goal')*/
      choice(name: 'MAVENGOAL', choices: 'clean\nclean package\nclean install', description: 'Enter the maven goal')
    }
    options{
        timeout(time: 30 , unit: 'MINUTES')
    }

        stages{
            stage('scm'){
                    steps{
                        git branch: 'release', url: 'https://github.com/spring-projects/spring-petclinic.git'
                    }
                }
            stage('build'){
                    steps{
                        powershell "mvn ${params.MAVENGOAL}"
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