pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    // Create virtual environment
                    // Note: If running on Windows agent, replace 'sh' with 'bat' and adjust paths (e.g., venv\\Scripts\\pip)
                    sh 'python3 -m venv venv'
                    
                    // Install dependencies if requirements.txt exists (optional but good practice)
                    // sh './venv/bin/pip install -r requirements.txt' 
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run the unit test using the python executable inside the virtual environment
                    // This avoids the need to explicitly "activate" the environment
                    sh './venv/bin/python test_baitap1.py'
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'Cleaning up workspace...'
                // Remove virtual environment
                sh 'rm -rf venv'
                // Clean entire workspace (requires Workspace Cleanup Plugin)
                cleanWs()
            }
        }
    }
}
