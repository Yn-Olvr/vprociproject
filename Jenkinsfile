pipeline {
    agent any
    tools{
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    
    environment {
        SNAP_REPO = 'snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'yann42'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.0.35'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                echo "Now Archiving."
                archiveArtifacts artifacts: '**/*.war'
            }
        }
        stage ('Test'){
            steps {
                sh 'mvn test'
            }
        }

        stage('Checkstyle Analysis'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}