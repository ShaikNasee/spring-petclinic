pipeline{
    agent{label "mvn-3.8.6"}
    triggers { upstream(upstreamProjects: 'starter-project', threshold: hudson.model.Result.SUCCESS) }
    stages{
        stage("source code management git"){
            steps{
                git branch: 'main', url: 'https://github.com/ShaikNasee/spring-petclinic.git'
            }
        }
        stage("maven build "){
            steps{
                sh " /usr/local/apache-maven-3.8.6/bin/mvn clean package "
            }
        }
        stage("archive artifacts"){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage("publish test reports"){
            steps{
                junit '**/TEST-*.xml'
            }
        }
    }
}