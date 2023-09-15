pipeline {
    agent {
        label 'BUilt-In Node'
    }
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f SMP/pom.xml clean package
            }
            stage('Build') {
            steps {
                // Use Maven to build your project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build and tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
 post {
        always {
            mail to: 'upadhyayganesh730@gmail.com',
            subject: "Job '${JOB_NAME}' (${BUILD_NUMBER}) is waiting for input",
            body: "Please go to ${BUILD_URL} and verify the build"
        }
        success {
            mail bcc: '', body: """Hi Team,

Build #$BUILD_NUMBER is successful, please go through the url

$BUILD_URL

and verify the details.

Regards,
DevOps Team""", cc: '', from: '', replyTo: '', subject: 'BUILD SUCCESS NOTIFICATION', to: 'upadhyayganesh730@gmail.com'
        }
        failure {
            mail bcc: '', body: """Hi Team,

Build #$BUILD_NUMBER is unsuccessful, please go through the url

$BUILD_URL

and verify the details.

Regards,
DevOps Team""", cc: '', from: '', replyTo: '', subject: 'BUILD FAILED NOTIFICATION', to: 'upadhyayganesh730@gmail.com'
        }
    }
}
