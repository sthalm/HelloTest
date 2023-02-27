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
                def tag = sh('git rev-parse --short HEAD')
                //sh('mvn package ')
            script {
              pom = readMavenPom(file: 'pom.xml')
              def pom_name = pom.build.finalName
            }
          }
        }
        stage('Test') {
            steps {
              echo "Test $pom_name $tag"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying $pom_name $tag"
            }
        }
    }
}
