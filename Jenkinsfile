pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'java17'
    }
    stages {
        stage('Download code Git') {
            steps {
                echo "download code from git"
                git branch: 'main', url: 'https://github.com/aasvi11/maven-jenkins4.git'
            }
        }
        stage('Build java project using maven') {
            steps {
                echo "build java project using maven"
                sh 'mvn clean package'
            }
        }
        stage('Archive artifacts') {
            steps {
                echo "archive the file"
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('build other project') {
            steps {
                echo "build other project using pipeline-deploy"
                build wait: false, job: 'pipeline-deploy'
            }
        }
    }
}
