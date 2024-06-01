pipeline {
    // agent { label 'Ansible-Master' }
	agent {
    docker {
      image 'abhishekf5/maven-abhishek-docker-agent:v1'
      args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
    }
  }
    
    stages {
    	/*stage ('Code Analysis'){
	    steps {
                withSonarQubeEnv('SonarQube') {
			sh 'mvn clean sonar:sonar'
		}
	    }
	}*/

	stage ('Compile Stage'){
	    steps {
	        withMaven(maven : 'Maven'){
		    sh 'mvn clean package'
		}
	    }
	}

	// stage ('Deploy to Nexus'){
	//     steps {
	//         withMaven(maven : 'Maven'){
	// 	    sh 'mvn deploy'
	// 	}
	//     }
	// }
	// stage ('Deploy to QA'){
	//     steps {
	//             sh 'sudo ansible-playbook /etc/ansible/main.yml'
	//     }
	// }

    }
}
