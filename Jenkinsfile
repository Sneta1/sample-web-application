pipeline{

      agent {
                docker {
                image 'maven'
                args '-v $HOME/.m2:/root/.m2'
                }
            }
        
        stages{

              stage('Quality Gate Status Check'){
                  steps{
                      script{
		    	    docker.withRegistry('https://hub.docker.com/', 'docker_credentials') {
			    image = docker.image('terraform:1.0')
			    image.pull()
			}
                 	}

               	 }  
              }	
		
            }	       	     	         
}
