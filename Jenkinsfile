node {
    stage('Checkout SCM') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: '/home/Documents/Proyek_Pertama_CI_CD/simple-python-pyinstaller-app']]])
    }
    stage('Build') {
        docker.image('python:2-alpine').inside {
            sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            stash(name: 'compiled-results', includes: 'sources/*.py*')
        }
    }
    stage('Test') {
        docker.image('qnib/pytest').inside {
            sh 'py.test --junit-xml test-reports/results.xml sources/test_calc.py'
        }
        junit 'test-reports/results.xml'
    }
}