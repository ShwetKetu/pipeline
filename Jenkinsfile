pipeline {
    agent { label 'maven-label' }
    tools {    
        maven "maven-3.6.2"
    }
    
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/vytec-app/app.git'
                sh "mvn -s settings.xml -Dmaven.test.failure.ignore=true clean deploy sonar:sonar -D sonar.host.url=http://18.117.83.250:31360/"
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
