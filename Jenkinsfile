pipeline {
agent any
tools {
maven 'Maven'
}
stages {
stage('Build') {
steps {
script {
sh "mvn clean package"
}
}
post {
success {
echo "Archiving the Artifacts"
archiveArtifacts artifacts: '*/target/.war'
}
}
}
stage('Deploy to Tomcat') {
steps {
script {
deploy adapters: [tomcat9(credentialsId: '51423a5f-3185-455f-8db8-16b07eb7dfaf', path: '', url: 'http://localhost:9090')], contextPath: 'one', war: '**/*.war'
}
}
}
}
}
