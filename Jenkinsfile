pipeline {
    agent any

    stages {
        stage('Disk Usage') {
            steps {
                script {
                    sh '''
                        echo "=== Information about disks ==="
                        df -h
                    '''
                }
            }
        }
        stage('Top Memory Process') {
            steps {
                script {
                    sh '''
                        echo "=== Process with highest memory usage ==="
                        ps aux --sort=-%mem | awk 'NR==2 {print "PID:",$2, "CPU:",$3"%", "MEM:",$4"%", "Command:",$11}'
                    '''
                }
            }
        }
    }

    post {
        always {
            sh 'echo "Monitoring finished"'
        }
    }
}