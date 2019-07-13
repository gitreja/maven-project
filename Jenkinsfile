pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
           }
    }
    {
        stage ('Compile Stage') {
            agent { label 'maven' }
            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean compile'
                  
                }
            }
        } 
    }
    {
    stage ('Test') {
           steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean test'
                }
            }
        }
    }
  {
    stage ('install') {
           steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean install'
                }
            }
        }
    } 
    {
    stage ('Deploy') {
           steps {
                sshagent (credentials: ['a2272c50-0d2b-4489-896a-a2341aed6f28']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@13.235.77.222:/var/lib/tomcat/webapps'
                }
            }
        }
    }
}










        
