currentBuild.displayName = "Final_Demo # "+currentBuild.number

   def getDockerTag(){
        def tag = sh script: 'git rev-parse HEAD', returnStdout: true
        return tag
        }

pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'java '    
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn clean install' 
	    }
        }
	stage('build'){
		      steps {
			      script{
                sh 'docker build . -t snetadocker/dockerapp:latest'
                withCredentials([string(credentialsId: 'docker_password', variable: 'docker_password')]) {
    
                sh '''docker login -u snetadocker -p $docker_password
                docker push snetadocker/dockerapp:latest
		'''
                }
                
			      }
		      }
    }
    }
}
