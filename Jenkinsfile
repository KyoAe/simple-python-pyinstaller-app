node {
    stage('Checkout SCM') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: '/home/Documents/Proyek_Pertama_CI_CD/simple-python-pyinstaller-app']]])
    }
    stage('Build') {
        docker.image('python:2-alpine'){
            sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            stash(name: 'compiled-results', includes: 'sources/*.py*')
        }
        // agent {
        //     docker {
        //         image 'python:2-alpine'
        //     }
        // }
        // steps {
        //     sh 'python -m py_compile sources/add2vals.py sources/calc.py'
        //     stash(name: 'compiled-results', includes: 'sources/*.py*')
        // }
    }
    stage('Test') {
        // agent {
        //     docker {
        //         image 'qnib/pytest'
        //     }
        // }
        // steps {
        //     sh 'py.test --junit-xml test-reports/results.xml sources/test_calc.py'
        // }
        // post {
        //     always {
        //         junit 'test-reports/results.xml'
        //     }
        // }
    }
}