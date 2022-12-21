pipeline{
    node("mvn-3.8.6")
    stages{
        stage("source code management git"){
            step{
                git branch: 'main', url: 'https://github.com/ShaikNasee/spring-petclinic.git'
            }
        }
        stage("build with maven "){
            steps{
                sh "mvn clean package "
            }
        }
        stage("archive artifacts"){
            step{
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