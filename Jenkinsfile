pipeline {
    agent any
    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk1.8.0_202'
        PYTHON_HOME = 'C:\\Users\\ouldache\\AppData\\Local\\Programs\\Python\\Launcher\\'
        PATH = "${env.PATH};${JAVA_HOME}\\bin;${PYTHON_HOME}"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mertilm/jenkins-data-pipeline.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo "Running on Unix"'
                        sh 'pip install virtualenv' 
                        sh 'py -m virtualenv madiha_env'
                        sh 'activate.bat'
                        sh 'python3 pip install pandas'
                        sh 'python data_analysis.py'
                    } else {
                        
                        bat 'echo "Running on Windows"'
                       // bat 'virtualenv temp'
                       // bat './temp/Scripts/acivate.bat'
                       // bat 'python'
                        bat 'pip install -r requirements.txt'
                        bat 'python data_analysis.py'  

                    }
                }
            }
        }
    }
}
