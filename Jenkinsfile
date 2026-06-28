pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // سحب الكود من المستودع
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                // بناء الصورة (تأكد من وجود Dockerfile في المستودع)
                sh 'docker build -t nodeapp:latest .'
            }
        }
        stage('Run Container') {
            steps {
                // تنظيف البيئة وتشغيل الحاوية
                sh 'docker stop nodeapp || true'
                sh 'docker rm nodeapp || true'
                sh 'docker run -d --name nodeapp -p 3000:3000 nodeapp:latest'
            }
        }
    }
}
