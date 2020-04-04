pipeline {
    parameters {
        configFileProvider([configFile(fileId: '406356bc-43d3-44a1-8834-5f337a1a546c', variable: 'MAVEN_GLOBAL_ENV')]) {}
    }
    agent any
    stages {
        stage('Build') {
            steps {
                    sh "mvn -s $MAVEN_GLOBAL_ENV -B -DskipTests clean package"
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -s $MAVEN_GLOBAL_ENV test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
