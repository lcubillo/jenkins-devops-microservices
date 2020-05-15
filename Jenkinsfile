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
    stages{
        stage('Build'){
            steps{
                echo "Build"
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