pipeline {
    agent { label 'agent1' }
    tools {    
        maven "maven"
    }
    
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/ShwetKetu/pipeline.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean install sonar:sonar -D sonar.host.url=http://54.212.210.238:9000/"
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
