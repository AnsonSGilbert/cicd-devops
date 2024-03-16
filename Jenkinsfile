pipeline {
agent any
tools {
maven 'Maven'
}
stages {
stage('Build') {
steps {
script {
bat "mvn clean package"
}
}
post {
success {
echo "Archiving the Artifacts"
archiveArtifacts artifacts: '**/target/*.war'
}
}
}
stage('Deploy to Tomcat') {
steps {
script {
deploy adapters: [tomcat9(credentialsId: 'a1b4d698-b39b-4a21-b58c-19f6523cc753', path: 'manager/text', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
}
}
}
}
}
