pipeline {
agent any
environment {
dockerCreds = credentials('dockerhub_login')
registry = "${dockerCreds_USR}/vatcal"
registryCredentials = "dockerhub_login"
dockerImage = "" // empty var, will be written to later
}
stages {
stage('Run Tests') {
steps {
sh 'npm install'
sh 'CI=true npm test'
}
}
stage('Build Image') {
steps {
script {
dockerImage = docker.build(registry)
}
}
