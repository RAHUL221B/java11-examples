pipeline {
    agent { label 'rahulnode' }
    triggers { cron('45 23 * * 1-5') }
    stages {
        stage('scm') {
            steps {
                git 'https://github.com/RAHUL221B/java11-examples.git'
            }
        }
        stage('build') {
            steps {
                sh '/usr/local/apache-maven-3.8.6/bin/mvn clean package'
            }
        }
    }
}    
