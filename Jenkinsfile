node {
	try {
        stage('Checkout') {
		checkout scm
        }
		stage('Environment') {
      		sh 'git --version'
      		sh 'docker -v'
      		sh 'printenv'
    	}
		stage('Build Docker test'){
     		sh 'docker build -t react-test -f Dockerfile.test --no-cache .'
    	}
    	stage('Docker test'){
      		sh 'docker run --rm react-test'
    	}
    	stage('Clean Docker test'){
      		sh 'docker rmi react-test'
    	}
        stage('Build') {
			sh 'docker -v'
			sh 'docker stop test || true && docker rm test || true'
            sh 'docker build -t test/node-web-react .'
			sh 'docker run -p 3006:3000 --name test -d test/node-web-react'
        }
	}
	catch (err) {
		throw err
	}
}
