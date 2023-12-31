pipeline {
    agent any
	
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
    stages {
        stage('Build') {
            steps {
                git credentialsId: 'pat_jenkins', poll: false, url: 'https://github.com/Soorajck8/WebApp.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
   
        stage('test') {
            steps {
                echo 'test app'
            }
        }
    
        stage('sonarqube') {
            steps {
                echo 'sonarqube World'
            }
        }
            stage('deploy') {
            steps {
                echo 'deploy app'
            }
        }
    }
}
