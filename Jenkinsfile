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
                mail from: "devops@rp.com",
                to: 'team@rp.com',
                subject: "Cloning code for project ${env.JOB_NAME} started",
                body: "${env.BUILD_URL}"

                git url:'https://github.com/RAHUL221B/java11-examples.git', branch: "${params.BRANCH_TO_BUILD}"
                
            }
        }
        stage('build') {
            steps {
                mail from: "devops@rp.com",
                to: 'team@rp.com',
                subject: "Build using maven for project ${env.JOB_NAME} started",
                body: "${env.BUILD_URL}"
                sh "/usr/local/apache-maven-3.8.6/bin/mvn ${params.MAVEN_GOAL}"
            }
        }
    }
    post {
        always {
            
            emailext attachLog: true,
                body: """<p> Executed: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER}\'
                </b></p><p>View console outpe at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}
                </a>"</p> <p><i>Build log is attached </i> </p>""",
                compressLog: true,
                replyTo: "do-not-reply@rp.com",
                to: "rpdevops@gmail.com",
                subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} -Status ${currentBuild.result}"   

             

        }
    }
}    
