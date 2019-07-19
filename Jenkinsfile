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
  stage ('build'){
      steps{
           withSonarQubeEnv('sonar') {
            withMaven(maven: 'localmaven'){
            sh 'mvn clean package sonar:sonar'
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
}









        
