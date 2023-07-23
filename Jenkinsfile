node {
    checkout scm
    withDockerContainer(image: 'python:2-alpine'){
    stage('Build') { 
    sh 'python -m py_compile sources/add2vals.py sources/calc.py'   
    }
    stage('Test') {
    sh 'pip install -U pytest' 
    sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
    sh "junit 'test-reports/results.xml'"
    }
  }
}
