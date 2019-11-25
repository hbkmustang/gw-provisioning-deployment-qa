
node () {

    stage ("CREATING INSTANCE QA") {
       sh "cd /home/ec2-user/GraduationWork"
       echo ansible playbook 
       sh "sh go.sh"
    }

    stage ("PROVISIONING") {
       sh "cd /home/ec2-user/GraduationWork"
       echo ansible playbook roles for provisioning QA instance
       // sh "sh go.sh"
       sh "ansible-playbook -i hosts --limit qa provisioning/site.yml"
    }

    stage ("DEPLOY") {
       echo ansible playbook should deploy latest version of application from Artifactory to QA environment - 8080 clear variant with no root user and 8081 docker variant
       sh "cd /home/ec2-user/GraduationWork"       
       sh "ansible-playbook -i ./hosts --limit -qa deployment/site.yml -e 'port=8080' --vault-password-file deployment/ansible-vault.pass"
    }

}
