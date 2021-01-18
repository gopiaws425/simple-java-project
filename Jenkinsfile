pipeline {

    agent any 

    stages {
        stage('Build1') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test1') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                   emailext body: '''${SCRIPT,template="groovy-html-larry-refactor.template"}''',
                             subject: "Job '${env.JOB_NAME} - ${env.BUILD_NUMBER}'",
                             to: 'trupti.ranjan.swain@gmail.com'
                }
            }
        }
    }
}
