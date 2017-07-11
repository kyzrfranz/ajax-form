pipeline {
    agent any

    tools{
        nodejs 'default'
    }

    stages {

    stage('Install'){
        steps{
            sh 'npm install -g polymer-cli'
            sh 'polymer install --variants'
        }
    }


    stage('Test'){
            steps{
                wrap([$class: 'Xvfb', autoDisplayName: true, debug: true, installationName: 'default',
                parallelBuild: true, timeout: 5000]) {
                  sh 'polymer test'
                }
            }
        }


        stage('Build'){
                    steps{
                        sh 'polymer build'
                    }
        }
    }
}
