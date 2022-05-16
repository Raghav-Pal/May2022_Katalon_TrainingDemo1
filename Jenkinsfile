pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                dir('/var/lib/jenkins/workspace/6_Jenkinsfile_Katalon_Docker'){
                    sh 'docker run -t --rm -v "$(pwd)":/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -retry=0 -testSuitePath="Test Suites/Suite2" -browserType="Chrome" -executionProfile="default" -apiKey="3315bf05-eb56-4f10-8716-6762fb652ee4"'
                }
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'Reports/**/*.*', fingerprint: true
            junit 'Reports/*/Suite2/*/*.xml'
        }
    }
}
