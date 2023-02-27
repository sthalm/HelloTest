pipeline {
    agent any
    tools {
      maven 'mvn3.6.3'
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
                sh('git branch -a')
                sh('git rev-parse --short HEAD')
                //sh('mvn package ')
            script {
              pom = readMavenPom(file: 'pom.xml')
              pom_name = pom.build.finalName
              tag = sh('git rev-parse --short HEAD')
            }
          }
        }
        stage('Test') {
            steps {
              echo "Test ${pom_name}"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying ${pom_name}"
            }
        }
    }
}
