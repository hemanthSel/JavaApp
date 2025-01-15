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
        stage('STG2: MAVEN UNIT TEST'){
            steps{
                script{
                     sh 'mvn test'
                }
            }
        }
        stage('STG3: Integration testing'){
            steps{
                script{
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('STG4: Maven Build'){
            steps{
                script{
                    sh 'mvn clean install'
                }
            }
        }
        stage('static code analysis'){
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-id') {
                        sh 'mvn clean package sonar:sonar'
}
                }
            }
        }
        // use waifForQualityGate step to get pipeline syntax
        stage('Quality Gate Status'){
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar-id'
                }
            }
        }
    }        
}