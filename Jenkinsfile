node('rahulnode') {
   properties([parameters([choice(choices: ['scripted', 'master', 'declarative'], description: 'branch to be built', name: 'BRANCH_TO_BUILD')])])
    stage('git') {
        git url: 'https://github.com/RAHUL221B/java11-examples.git',branch: "${params.BRANCH_TO_BUILD}"
    }
}    