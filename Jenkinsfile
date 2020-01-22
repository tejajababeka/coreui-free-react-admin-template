node {
	try {
        stage('Checkout') {
		checkout scm
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
