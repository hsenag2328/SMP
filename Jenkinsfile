node{
    stage('SCM Checkout'){
        git 
    }
    stage('Compile-Package'){
        //Get maven home path
        def mvnHome = tool name: maven-3.6.3', type: 'maven'
        sh "${mvnHome}/bin/mvn package
    }
    stage{'Email Notification'){
        Regards,
            Ganesh""", cc: '', from: '', replyTo: '', subject: 'BUILD SUCCESS NOTIFICATION', to: 'upadhyayganesh730@gmail.com'
        }
        failure {
            mail bcc: '', body: """Hi Welome to Jenkins email alert
        Thanks
        Ganesh,

Build #$BUILD_NUMBER is unsuccessful, please go through the url

$BUILD_URL

and verify the details.

Regards,
    Ganesh""", cc: '', from: '', replyTo: '', subject: 'BUILD FAILED NOTIFICATION', to: 'upadhyayganesh730@gmail.com'
        }
    }
}
