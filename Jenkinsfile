 
pipeline {
    agent any

    stages {
        stage('---Clean---') {
            steps {
                echo 'Cleaning..'
            }
        }
        stage('---Test---') {
            steps {
                echo 'Testing..'
            }
        }
        stage('---package--') {
            steps {
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
                  echo 'Packaging..'
            }
        }
     stage('---Publish--') {
            steps {
                nexusPublisher nexusInstanceId: 'LocalNexus-3', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'C:\\Users\\011391\\.jenkins\\workspace\\GroovyPipelineSpringBoot\\target\\SpringBootRestApiExample-1.0.0.jar']], mavenCoordinate: [artifactId: 'Drop59', groupId: 'CDR_central', packaging: 'jar', version: '$FILENAME+$VERSION']]]
            }
        }
    }
	post { 
	  stage('---CLEAN WS--') {
        always { 
            cleanWs()
        }
		}
    }
}
