pipeline {
    agent any
    
    tools
    {
       maven "Maven"
    }
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/devops4solutions/CI-example.git'
             
          }
        }    
        
         stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }     
               
        stage('Ansible Deploy') {
             
            steps {        
               sh "ansible-playbook main.yml -i inventories/dev/hosts --user jenkins --key-file ~/.ssh/id_rsa"                    
            }
        }
    }
}
