pipeline {
    agent any
    stages {
        stage(Checkout) {
            steps { checkout scm }
        }
        stage(Build) {
            steps {
                echo Building the app...
                sh python3 --version
            }
        }
        stage(Test) {
            steps {
                echo Running tests...
                sh python3 test_app.py
            }
        }
        stage(Deploy) {
            steps {
                echo Deploying...
                sh python3 app.py
            }
        }
    }
}
