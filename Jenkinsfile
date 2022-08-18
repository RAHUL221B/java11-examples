pipeline {
    agent { label 'rahulnode' }
    triggers { upstream(upstreamProjects: 'starter project', threshold: hudson.model.Result.SUCCESS) }
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