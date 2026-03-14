pipeline{
    agent any
    tools {
        maven 'Maven3'
        jdk 'java21'
    }
    stages{
        stage('Download code'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/IFSCA/maven-jenkins10.git']])
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Generate artifact'){
            steps{
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Trigger Deploy pipeline'){
            steps{
                build wait: false, job: 'Deploy-pipeline'
            }
        }
    }
}
