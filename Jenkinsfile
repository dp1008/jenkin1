pipeline {
    agent any
 tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                sh "mvn --version"
                sh "mvn test"
    //            sh "mvn --version"
        //        slackSend channel: 'youtubejenkins', message: 'Job Started'
          echo "executing test"      
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                echo "executing build" 
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
             //  deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://192.168.0.118:8080')], contextPath: '/app', war: '**/*.war'
              
             echo "executing deploy on test" 
             deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetail1', path: '', url: 'http://192.168.233.128:9090')], contextPath: '/app', war: '**/*.war'
            }
            
        }
   
    }        

    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
          //   slackSend channel: 'youtubejenkins', message: 'Success'
        }
        failure{
            echo "========pipeline execution failed========"
            // slackSend channel: 'youtubejenkins', message: 'Job Failed'
        }
    }
 }