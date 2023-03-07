pipeline {
    agent { label 'agent1' }
    tools {
        maven "maven"
    }

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/ShwetKetu/pipeline.git'
            }
        }
    stage('Build') {
            steps {
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
