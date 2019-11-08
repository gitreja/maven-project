pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/gitreja/maven-project.git'
           }
    }
    {
        stage ('Compile Stage') {
            agent { label 'maven' }
            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                  
                }
            }
        } 
    }
    {
    stage ('Test') {
           steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean test'
                }
            }
        }
    }
    {
  stage ('build && sonarqube analysis'){
      steps{
           withSonarQubeEnv('sonar') {
            withMaven(maven: 'maven'){
            sh 'mvn clean package sonar:sonar'
            }
           }
      }
  }
    }
 
  {
    stage ('install') {
           steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean install'
                }
            }
        }
    } 
}









        
