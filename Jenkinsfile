def buildno = BUILD_NUMBER

pipeline {
    agent any
	
    stages {
	   
	
	stage('Building image') {
            steps{
                script {
		          
			  sh "docker build -t yoshithadocker/mydockerrepo:${buildno} ."
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
	  
	
       stage('K8S Deploy') {
             steps{   
              script {
                    withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'kubeconfig', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                                 // sh "kubectl apply -f ./test/storageClass.ya
                           }
             }
            }
        }

     }

}
