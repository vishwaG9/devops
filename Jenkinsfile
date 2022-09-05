pipeline {
    agent any

    stages {
        stage('Clean the workspace') {
            steps {
                cleanWs()
            }
            
        }
        stage('Code Checkout') {
            steps {
                //checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'a0a92755-710d-4e73-9ab6-a7a976eb99ad', url: 'https://github.com/debasishdas033/maven-app.git']]])
               bat 'git clone https://github.com/dd18/maven-test-app.git'
                
                
                }
        }
        stage('Code Build') {
            steps {
            bat '''
                cd %WORKSPACE%
                cd maven-test-app
                mkdir target
                mvn package
            '''
        }
        }
        stage('Code Deployment') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '508fc250-0726-4dcf-b4ef-2fc5b0666d2f', path: '', url: 'http://localhost:8085')], contextPath: 'SpringMVC4', war: '**/SpringMVC4.war'
            }
        }
                
    }
}
