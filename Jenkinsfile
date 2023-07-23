pipeline {
    agent any
    
    tools {
        maven 'localMaven'
        jdk 'Java8'
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('Deliver to Ansible') {
            scp ${workspace}target/*.war root@3.108.41.82:/etc/ansible/App
        }
    }
}
