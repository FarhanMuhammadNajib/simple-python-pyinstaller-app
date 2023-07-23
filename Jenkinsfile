node {
    checkout scm
    stage('Build') { 
    withDockerContainer(image: 'python:2-alpine'){
    sh 'python -m py_compile sources/add2vals.py sources/calc.py'   
        }
    }
    stage('Test') {
    sh 'sudo apt-get install pip && pip install pytest'
    sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
    sh "junit 'test-reports/results.xml'"
    }
  }
