pipeline {
    agent any
    stages {
        stage('clone my code'){
          git 'https://github.com/gitreja/maven-project'
           }
        stage ('complie my code'){
            
            steps{
                withmaven(maven :'localmaven') {
                    sh 'mvn compile'
                    
                }
            }
        }
    }
}               
                

         
