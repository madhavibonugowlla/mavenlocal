pipeline {
    agent any

    stages {
        stage('git_clone') {
            steps {
                sh '''
                echo 'cloning code from git'
                rm -rf mavenlocal
                git clone 'https://github.com/madhavibonugowlla/mavenlocal.git'
                '''
            }
        }
        stage('BUILD') {
            steps {
                sh '''
                echo 'here compiling the dev code'
                pwd
                ls -ll
                cd mavenlocal
                mvn clean
                mvn compile
                '''
            }
        }
        stage('test') {
            steps {
                sh '''
                echo 'validating test cases'
                pwd
                ls -ll
                cd mavenlocal
                mvn test
                '''
            }
        }
      stage('sonar') {
            steps {
                sh '''
                echo 'validating sonar code coverage'
                pwd
                ls -ll
                cd mavenlocal
                mvn sonar:sonar
                '''
            }
        }
        stage('package') {
            steps {
                sh '''
                echo 'creating package'
                pwd
                ls -ll
                cd practice
                mvn package
                '''
            }
        }
        stage('jfrog') {
            steps {
            sh '''
            echo 'uploading packages to jfrog repo'
            '''
            }
        }
    }
}
