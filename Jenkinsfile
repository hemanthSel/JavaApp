pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                   git branch: 'main', url: 'https://github.com/hemanthSel/JavaApp.git'
                  
                    //git branch: 'main', url: 'https://github.com/vikash-kumar01/mrdevops_javaapplication.git' 
                }
            }
        }        
        stage("STG2: MAVEN TEST"){
            steps{
                scripts{
                     'mvn test'
                }
            }
        }
    }        
}