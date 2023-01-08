pipeline {
        agent any
        tools{
            maven 'maven_3_8_7'
        }
        stages{
            stage('build maven'){
		steps{
                	checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/AymenOpenGod/DevOps-Project.git']])
                	sh './mvnw package'

		    }
            
        }
        
        stage('build docker image'){
	        steps{
		        script{   
		                sh 'whoami'
			            sh 'docker build -t fathallahaymen/webapp .'		                

		                }
	            }
    }
        stage('push image to Hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dokerhubpwd')]) {
                    sh 'docker login -u fathallahaymen -p ${dokerhubpwd}'
                    }
	                sh 'docker push fathallahaymen/webapp'

                    }	
                }      
        }


    }
}
    
    


