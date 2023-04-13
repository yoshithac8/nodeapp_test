def buildno = BUILD_NUMBER

pipeline {
    agent any
	
    stages {
	   
	
	stage('Building image') {
            steps{
                script {
		          
			  sh "docker build -t yoshithadocker/nodejs:${buildno} ."
                     }
                  }
              }
	      
	 stage('push to repo') {
            steps{
                script {
			         withCredentials([usernamePassword(credentialsId: 'yoshithadocker', passwordVariable: 'dockerpassword', usernameVariable: 'yoshithadocker')]) {
			                 sh 'docker login -u yoshithadocker -p ${dockerpassword}'
                                         sh "docker push yoshithadocker/nodejs:${buildno}"
                          }
                  }
              }
          }

     }

}
