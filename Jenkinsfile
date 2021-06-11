pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mymaven"
        //JDK "myjava"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/devops-trainer/DevOpsClassCodes.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
                
            }
        }
        stage('Codereview') {
            steps {
                sh 'mvn pmd:pmd'
            }    
        } 
        stage('Unittest') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Metriccheck') {
            steps {
                sh 'mvn cobertura:cobertura -Dcobertura:report:formula=xml'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }   
        
}
