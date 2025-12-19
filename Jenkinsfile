pipeline {
    agent any
    tools{
        maven 'maven 3.9.6'
    }
    
    stages{
        stage("build"){
            steps{
                echo 'step 1'
                sh 'mvn compile'
            }
        }
        
        stage("test"){
            steps{
                echo 'step 2'
                sh 'mvn test'
            }
        }
        
        stage("package"){
            steps{
                echo 'step 3'
                sh 'mvn package -DskipTests'
            }
        }
    }
    post{
        always{
            echo 'This pipeline is completed..'
        }
    }
}
    
