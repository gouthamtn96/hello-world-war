pipeline {
    agent { label 'java' } 
    stages {
        stage('setting up parameter') {
            steps {
                script {
                    properties([
                        parameters([
                            choice(
                                choices: ['test', 'development'] ,
                                name : 'slaves'
                                )
                            ])
                        ])
                }
            }
        }
        stages('clone step') {
            steps {
                sh 'rm -rf hello-world-war'
              sh 'git clone https://github.com/gouthamtn96/hello-world-war.git'
            }
        }
      stage('build step') {
        steps {
          sh 'mvn package'
        }
      }
        stage('deploy step') {
      steps {
        sh 'sudo cp /home/slave1/workspace/helloworld/target/hello-world-war-1.0.0.war /opt/apache-tomcat-9.0.64/webapps'
      }
    }
}
}
