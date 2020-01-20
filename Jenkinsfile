node {
	try {
        stage('Checkout') {
		checkout scm
        }
        stage('Build') {
		sh 'docker -v'
                sh 'docker build -t test/node-web-app .'
		sh 'docker run -p 3001:3000 -d test/node-web-app'
            }
	}
	catch (err) {
		throw err
	}
}
