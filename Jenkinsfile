pipeline {  
    agent any  
    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git 'https://github.com/PavanGandham/SpringBootWAR.git'
                    echo "Checkout successful";
                } 
            }
            stage ('Validate') {  
                steps{
                    sh 'mvn clean'
                    sh 'mvn validate'
                    echo "Validated successful";
                    
                } 
            }      
            stage ('Compile') {  
                steps{
                    sh 'mvn compile'
                    echo "test successful";
                    
                } 
            }
            stage ('Build') {  
                steps{
                    sh 'mvn package'
                    echo "build successful";
                    
                } 
            }
            stage ('Test') {  
                steps{
                    sh 'mvn test'
                    echo "test successful";
                } 
            }
            
        stage ('Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'pavan', path: '', url: 'http://ec2-54-211-192-201.compute-1.amazonaws.com:8081')], contextPath: 'booking-app', war: '**/*.war'
            echo "Deploy successful";
            }
        }
        stage ('Monitor') { 
            steps{ 
                echo "Now you can monitor!";
            }
        }
    }
}
