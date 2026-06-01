pipeline {

agent any

stages {

stage('Clone') {
steps {
git 'https://github.com/chavvakulanikhil/super_market.git'
}
}

stage('Build Docker Image') {
steps {
sh 'docker build -t supermarket-app .'
}
}

stage('Stop Old Container') {
steps {
sh '''
docker stop supermarket-container || true
docker rm supermarket-container || true
'''
}
}

stage('Deploy Container') {
steps {
sh '''
docker run -d \
--name supermarket-container \
-p 80:80 \
supermarket-app
'''
}
}

}

}
