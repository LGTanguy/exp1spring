pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage ("Clean up") {
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo") {
            steps {
                sh "git clone https://github.com/LGTanguy/exp1spring.git"
            }
        }
        stage ("Generate backend image") {
            steps {
                dir("exp1spring") {
                    sh "mvn clean install"
                    sh "docker build -t exp1spring ."
                }
            }
        }
        stage ("Run docker compose") {
            steps {
                dir("exp1spring") {
                    sh "docker compose up -d"
                }
            }
        }
    }
}
