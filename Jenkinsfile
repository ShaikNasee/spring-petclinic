pipeline{
    agent{label "mvn-3.8.6"}
    stages{
        stage("source code management git"){
            steps{
                git branch: 'main', url: 'https://github.com/ShaikNasee/spring-petclinic.git'
            }
        }
        stage("maven build "){
            steps{
                sh "mvn clean package "
            }
        }
        stage("archive artifacts"){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage("publish test reports"){
            steps{
                junit '**TEST/*.xml'
            }
        }
    }
}