pipeline {
    agent any 
    // agent is where my pipeline will be eexecuted
    tools {
        //install the maven version configured as m2 and add it to the path
        maven "m3"
    }
    stages {
        stage('pull from scm') {
            steps {
            git credentialsId: 'gopal1409', url: 'https://github.com/gopal1409/jenkins-ansible-tomcat.git'
            }
        }
         stage('build it') {
            steps {
            sh 'mvn clean package'
            }
        }
        stage('install tomcat') {
            steps {
              ansiblePlaybook credentialsId: 'ansible-jenkins', disableHostKeyChecking: true, inventory: 'dev.inv', playbook: 'tomcat.yml'
            }
        }
    }
}
