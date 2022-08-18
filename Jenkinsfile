node('rahulnode') {
   properties([pipelineTriggers([cron('0 */3 * * 0,6')])])
    stage('git') {
        git 'https://github.com/RAHUL221B/java11-examples.git'
    }
}    