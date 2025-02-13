pipeline {
	agent any
	tools {
		maven 'maven 3.9.9'
		jdk 'Java JDK 17'
	}
	stages {
		stage("clean") {
			steps {
				echo "Start Clean"
				sh "mvn clean"
			}
		}
		stage("build") {
			steps {
				echo "Start build"
				sh "mvn install -DskipTests"
			}
		}
        stage('deployment') {
			steps {
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://localhost:8090')], contextPath: 'maven-web-project2', war: '**/*.war'
			}
		}
	}
}