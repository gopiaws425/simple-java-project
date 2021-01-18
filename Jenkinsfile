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
                   emailext body: 'Test Message',
                             subject: 'Test Subject',
                             to: 'Gopisdevops1@gmail'
                }
            }
        }
    }
}
