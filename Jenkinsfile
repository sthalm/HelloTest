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
                sh('git branch')
                sh('git rev-parse --short HEAD')
                //sh('mvn package ')
            script {
              pom = readMavenPom(file: 'pom.xml')
              def pom_name = pom.finalName
            }
          }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                echo "Application name is ${pom.name}"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
