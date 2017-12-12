#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {
	
	    stage('envset'){
	     withEnv([
            "devopsName='Jenkins DevOps'",
            'emailTo=devopstrainingblr@gmail.com',
            'emailFrom=devopstrainingblr@gmail.com'
	    ])
	    }
       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          sh 'mvn deploy'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }
       stage('mail'){

         def subject = "${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
    def summary = "${subject} (<${env.BUILD_URL}|Open>)"
    def details = """<p>${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Error: ${errorMessage}</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>"""
    emailext recipientProviders: [[$class: 'DevelopersRecipientProvider']], subject: subject, body: details
       }

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           def subject = "${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
    def summary = "${subject} (<${env.BUILD_URL}|Open>)"
    def details = """<p>${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Error: ${errorMessage}</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>"""
    emailext recipientProviders: [[$class: 'DevelopersRecipientProvider']], subject: subject, body: details

        throw err
    }
}
