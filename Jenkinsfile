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
    agent any
    //agent {
    //    docker {
    //        image  'maven:3.6.3'
    //    }
    //}
    environment {
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn --version'
                sh 'docker version'
                echo "Build"
                echo "PATH = $PATH"
                echo "build_number = $env.BUILD_NUMBER"
                echo "BUILD_ID = $env.BUILD_ID"
                echo "JOB_NAME = $env.JOB_NAME"
                echo "BUILD_TAG = $env.BUILD_TAG"
                echo "BUILD_URL = $env.BUILD_URL"
            }
        }
        stage('Compile'){
            steps{
                sh "mvn clean compile"
            }
        }
        stage('Test'){
            steps{
                sh "mvn test"
            }
        }
        stage('Integration Test'){
            steps{
                sh "mvn failsafe:integration-test failsafe:verify"
            }
        }
        stage('Package'){
            steps{
                sh "mvn package -DskipTests"
            }
        }
        stage ('Build docker image'){
            //"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
            steps{
                script{
                    dockerImage = docker.build("lcubillo/currency-exchange-devops:${env.BUILD_TAG}")
                }
            }
        }
        stage ('Push docker image'){
            steps{
                script{
                    docker.withRegistry('','dockerhub'){
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
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