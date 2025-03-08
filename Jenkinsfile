pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Echo Version'){
            steps{
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                //git branch: 'main', url: 'https://github.com/krishtambe/jenkins-hello-world.git'

                // Run Maven on a Unix agent.
                sh "mvn clean package -DskipTests=True"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Unit Test'){
            steps{
                for(int i=0; i <60; i++){
                    echo "${ i + 1 }"
                    sleep 1
                }
                sh 'mvn test'
            }
        }
    }
}
