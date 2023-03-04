pipeline {
    agent { label 'agent1' }
    tools {    
        maven "maven"
    }
    
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/ShwetKetu/pipeline.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean install"
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
