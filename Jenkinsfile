pipeline {

    agent any

    parameters{
	string(name: 'SPEC', defaultValue: "cypress/e2e/**/**", description: "Enter the scripts path")
	choice(name: 'BROWSER', choices: ['chrome', 'edge', 'firefox'], description: "Choose the browser")

    }

    options{
	ansiColor('xterm')
    }

    stages{
	stage('Build'){
	    echo "Building the application"
        }
        stage('Testing'){
	    steps{
	        sh "npm i"
	        sh "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
	    }
	}
	stage('Deploying'){
	    echo "Deploy the application"
	    }
    }

	post{
	    always{
		publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, icon: '', keepAll: true, reportDir: 'cypress/reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
	    }
	    
	}
	
}
	


