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
                        ps aux --sort=-%mem | awk 'NR==2 {printf "PID: %s | CPU: %s%% | MEM: %s%% | Command: %s\n", $2, $3, $4, $11}'
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