pipeline {

		environment {
    		imagename = "dockercomposerfile/cd-project"
   			registryCredential = 'dockerhub'
   			dockerImage = ''
  		}
  		
        agent any
        
        tools{
                maven 'Maven'
        }
        
        stages{
           
        	  stage('Building image') {
      				steps{
       					 script {
       						   dockerImage = docker.build imagename
      						  }
      					}
   				 }
   				 
     		   stage('Deploy Image') {
 				     steps{
       					 script {
        						  docker.withRegistry( '', registryCredential ) {
          						  dockerImage.push("$BUILD_NUMBER")
         					      dockerImage.push('latest')

        					      }
       					 		}
    					  }
   				 }

  
        }

}
