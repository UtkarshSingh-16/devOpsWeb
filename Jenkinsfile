@Library ('myLibrary')_
pipeline {
    agent any
    
    tools {
        maven 'localMaven'
    }

stages{
        stage('Build'){
            steps {
                build-demo()
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ("Deploy to Staging"){
                    steps {
                        echo "Deploy to Staging"
                    }
                }
            }
        }
    }
}
