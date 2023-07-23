node {
    checkout scm
    stage('Build') { 
    withDockerContainer(image: 'python:2-alpine'){
    sh 'python -m py_compile sources/add2vals.py sources/calc.py'   
        }
    }
    stage('Test') {
    withDockerContainer(image: 'python:2-alpine'){
    sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
        }
    }
    post {
      always {
        junit 'test-reports/results.xml'
    }
  }
}
