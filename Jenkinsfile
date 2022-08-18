pipeline {
    agent { label 'rahulnode' }
    triggers { cron('45 23 * * 1-5') }

    parameters {
        string(name: 'MAVEN_GOAL', defaultValue: 'package', description: 'This is maven goal' )
        choice(name: 'BRANCH_TO_BUILD', choices: ['declarative', 'master', 'scripted'], description: 'Branch to build')
    }
    stages {
        stage('scm') {
            steps {
                git url:'https://github.com/RAHUL221B/java11-examples.git', branch: "${params.BRANCH_TO_BUILD}"
            }
        }
        stage('build') {
            steps {
                sh '/usr/local/apache-maven-3.8.6/bin/mvn ${params.MAVEN_GOAL}'
            }
        }
    }
}    
