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
	
        
    }
}

