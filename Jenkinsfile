pipeline {
    agent any

    stages {
        stage('Clone Git Project') {
            steps {
                echo 'NOT Cloning Katalon project from Repository'
//              git 'https://github.com/Raghav-Pal/May2022_Katalon_TrainingDemo1'
            }
        }
         stage('Test') {
            steps {
                dir('/var/lib/jenkins/workspace/15_Katalon_Jenkinsfile_Docker_Demo/'){
                    sh 'docker run -t --rm -v "$(pwd)":/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -retry=0 -testSuitePath="Test Suites/Suite1" -browserType="Chrome" -executionProfile="default" -apiKey="3315bf05-eb56-4f10-8716-6762fb652ee4"'
                }
            }
        }
    }
        post {
        always {
            archiveArtifacts artifacts: 'Reports/**/*.*', fingerprint: true
            junit 'Reports/*/Suite1/*/*.xml'
        }
    }
}
