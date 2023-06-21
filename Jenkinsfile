pipeline {
    agent any
    tools{
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    
    environment {
        SNAP_REPO = 'snapshot'
        NEXUS_USER = 'admin'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.0.35'
        NEXUS_PORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }
}