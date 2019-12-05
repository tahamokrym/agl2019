pipeline {
    agent any
    tools {
     maven 'apache-maven-3.5.4'   
     jdk 'jdk1.8.0_161'
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn package'
               
            }
        }
        stage('couverture') {
            steps {
               
                bat 'mvn javadoc:javadoc cobertura:cobertura -Pmetrics'
                
            }
             post {
                  always {
                        cobertura coberturaReportFile: '**/target/site/cobertura/coverage.xml'
                        cleanWs()
                        }
                  }
        }
        
    }
}
