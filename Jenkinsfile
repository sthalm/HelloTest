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
              def pom_name = pom.build.finalName
              def customImage = docker.build("${pom_name}:latest")
            }
          }
        }
        stage('Docker Build') {
            steps {
              echo "Dockerbuild"
              //oc process -f bc.yaml -p NAME="${pom_name}" | oc apply -f -
              //binaryBuild(buildConfigName: "${pom.name}", buildFromPath: ".")
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
