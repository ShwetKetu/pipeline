pipeline {
    agent any
    tools {    
        maven "maven-3.6.2"
    }
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/vytec-app/app.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
            post {  
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
