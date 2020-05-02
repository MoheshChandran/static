pipeline {
     agent any
     stages {
		 stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
		 
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-southeast-1',credentials:'aws-static') {
                  sh 'echo "Hello World with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-jenkin-project-3')
                  }
              }
         }
     }
}
