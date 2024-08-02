pipeline {
    agent { label 'slave'}
    tools{
        maven 'maven-test'
    }
    stages{
        stage ('checkout scm'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('deploy'){
            steps{
                sshagent(['tomcat-web-application']) {
                sh "scp -o StrictHostkeyChecking=no target/maven-web-application.war ec2-user@54.163.28.4:/opt/tomcat9/webapps"


                }
            }
        }
    }
}
