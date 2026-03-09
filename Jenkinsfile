pipeline{
    tools{
        jdk 'JDK17'
        maven 'Maven-3'
    }

    agent any

    stages{

        stage('Checkout'){
            steps{
                echo 'Cloning repository...'
                git 'https://github.com/2300032999cse2-eng/DevOpsClassCodes.git'
            }
        }

        stage('Compile'){
            steps{
                echo 'Compiling project...'
                sh 'mvn compile'
            }
        }

        stage('Code Review'){
            steps{
                echo 'Running PMD analysis...'
                sh 'mvn pmd:pmd'
            }
        }

        stage('Unit Test'){
            steps{
                echo 'Running tests...'
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package'){
            steps{
                echo 'Packaging application...'
                sh 'mvn package'
            }
        }
    }
}
