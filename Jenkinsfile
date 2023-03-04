pipeline {
    agent { label 'agent1' }
    tools {    
        maven "maven"
    }
    
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/ShwetKetu/pipeline.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean install sonar:sonar -D sonar.host.url=http://54.212.210.238:9000/ -D sonar.login=sqa_6c1738f8bc54718f184d56df7cefac799c7d66ae"
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
