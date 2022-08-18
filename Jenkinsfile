node('rahulnode') {
    properties([pipelineTriggers([upstream('"starter project", ')])])
    stage('git') {
        git 'https://github.com/RAHUL221B/java11-examples.git'
    }