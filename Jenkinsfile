#!groovy

node {
	   
	stage('Checkouting'){

          checkout scm
       }

       stage('BuildArtifact'){

          sh 'mvn install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }
       
}
