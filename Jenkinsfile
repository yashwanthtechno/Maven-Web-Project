pipeline {
    agent any

    stages {
        stage('Compile Stage') {
            steps {
                echo 'Comple Stage starts...'
				withMaven(maven : 'maven_3_5_2'){
				 sh 'mvn clean compile'
				echo 'Comple Stage ends...'
				}
            }
        }
        stage('Testing Stage') {
            steps {
                echo 'Testing Stage starts...'
				withMaven(maven : 'maven_3_5_2'){
				 sh 'mvn test'
				echo 'Testing Stage ends...'
				}
            }
        }
        stage('Install Stage') {
            steps {
                echo 'Install Stage starts...'
				withMaven(maven : 'maven_3_5_2'){
				 sh 'mvn install'
				echo 'Install Stage ends...'
				}
            }
        }
	 stage('Deploy Stage') {
            steps {
                echo 'Install Stage starts...'
				withMaven(maven : 'maven_3_5_2'){
				 sh 'mvn deploy'
				echo 'Deploy Stage ends...'
				}
            }
        }   
        stage('SonarQube Scanner Stage') {
            steps {
                echo 'Deploymnet Stage starts...'
				 sh 'mvn sonar:sonar'
				echo 'Deploymnet Stage ends...'
            }
        }
    
    }
	post {
    success {
      
      emailext (
          subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
          recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        )
    }
failure {
     
      emailext (
          subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
          recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        )
    }
}	
}	
