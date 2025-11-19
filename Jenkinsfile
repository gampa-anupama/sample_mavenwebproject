pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build Project') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo "Deploying WAR to Tomcat..."
                bat 'copy target\\*.war C:\\Users\\anupa\\Downloads\\apache-tomcat-9.0.112\\apache-tomcat-9.0.112\\webapps\\'
            }
        }

        stage('Restart Tomcat') {
            steps {
                bat 'C:\\Users\\anupa\\Downloads\\apache-tomcat-9.0.112\\apache-tomcat-9.0.112\\bin\\shutdown.bat || exit 0'
                bat 'C:\\Users\\anupa\\Downloads\\apache-tomcat-9.0.112\\apache-tomcat-9.0.112\\bin\\startup.bat'
            }
        }

        stage('Deployment Status') {
            steps {
                echo "Visit your app at http://localhost:8081/YOUR_WAR_NAME"
            }
        }
    }
}
