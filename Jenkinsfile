pipeline {
    agent any
    
    stages {
        stage('Test Build') {
            steps {
                echo 'Pipeline is running successfully!'
            }
        }
    //     stage('Semgrep scan') {
    // 		steps {
    //     		script {
    //         			def status = sh(
    //             		script: "docker run -v ${WORKSPACE}:/src --workdir /src returntocorp/semgrep-agent:v1 semgrep-agent --config auto",
    //             		returnStatus: true
    //         		)

    //         			if (status == 1) {
    //             			echo "Semgrep exited with code 1. Marking build as UNSTABLE."
    //             			currentBuild.result = 'UNSTABLE'
    //         			} else if (status != 0) {
    //             			error "Semgrep exited with code ${status}. Failing build."
    //         			}
    //     		}
    // 		}
	// }
	// stage('OWASP Dependency-Check Vulnerabilities') {
    //   		steps {
    //     		dependencyCheck additionalArguments: ''' 
    //                 		-o './'
    //                 		-s './'
    //                 		-f 'ALL' 
    //                 		--prettyPrint''', odcInstallation: 'owasp-dc'
        
    //     		dependencyCheckPublisher pattern: 'dependency-check-report.xml'
    //   		}
    // 	}
		stage('Gitleks scan') {
      		steps {
        		sh '''
					docker run -v  ${WORKSPACE}:/path zricethezav/gitleaks:latest detect --source="/path" -v --no-git --report-format json --report-path secrets.json
				'''
      		}
    	}
    }
}

