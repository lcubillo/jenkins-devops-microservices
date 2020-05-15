//SCRIPTED
//node {
//	stage('Build') {
//		echo "Build"
//	}
//	stage('Test') {
  //  		echo "Test"
    //	}
//	stage('Integration Test') {
//		echo "Integration Test"
//	}
//}

//DECLARATIVE
pipeline{
    //agent any
    agent {
        docker {
            image  'maven:3.6.3'
        }
    }
    stages{
        stage('Build'){
            steps{
                //sh 'mvn --version'
                echo "Build"
                echo "PATH = $PATH"
                echo "build_number = $env.BUILD_NUMBER"
                echo "BUILD_ID = $env.BUILD_ID"
                echo "JOB_NAME = $env.JOB_NAME"
                echo "BUILD_TAG = $env.BUILD_TAG"
                echo "BUILD_URL = $env.BUILD_URL"
            }
        }
        stage('Test'){
            steps{
                echo "Test"
            }
        }
        stage('Integration Test'){
            steps{
                echo "Integration Test"
            }
        }
    }
    post {
        always{
            echo 'Im awesome. I run always'
        }
        success {
            echo 'everything is ok.'
        }
        failure {
            echo 'Something is wrong.'
        }
    }
}