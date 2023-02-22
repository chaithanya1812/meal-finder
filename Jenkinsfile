pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    stages{
        stage('GitHub-Webhook'){
            steps{
                script{
                    properties([pipelineTriggers([githubPush()])])
                }
            }
        }
        stage('Git-clone'){
            steps{
                git branch: 'FIRST', url: 'https://github.com/chaithanya1812/test9-Ansible.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        /*
        stage('SonarqubeReport'){
            steps{
                sh 'mvn sonar:sonar'
            }
        }
        */
    
        stage('Nexus-Artifact'){
            steps{
                sh 'mvn deploy'
            }
        }
        stage('Publish-artifact-Ansible-Master'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'AnsibleMaster', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook  tomcat.yaml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '/target/', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
               
    }   
}
