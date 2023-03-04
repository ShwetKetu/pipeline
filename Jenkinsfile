pipeline {
    agent { label 'agent1' }
    tools {    
        maven "maven"
    }
    
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/ShwetKetu/pipeline.git'
                sh "mvn -s settings.xml -Dmaven.test.failure.ignore=true clean deploy"
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
