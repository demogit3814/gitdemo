pipeline {
    agent any
    parameters {
        choice(name: 'Environment',choices:['Dev', 'Test', 'Prod'], description: "Choose your environment")
        password(name:'Password', defaultValue: 'API123', description:'Password Stage')
        text(name:'log', defaultValue: 'This is log', description: "enter build log detail")
    }
    stages {
        stage ('DevStage') {
            when {
                expression { params.Environment == 'Dev'}
            }
            steps {
                echo "Bulding Dev stage without prompt"
                echo "Hello"
                echo "password is ${params.Password}"
                echo "${params.log}"
            }
        }
        stage ('TestStage') {
            when {
                expression {params.Environment == 'Test'}
            }
            steps {
                echo "Building Test stage without prompt"
            }
        }
        stage ('ProdStage') {
            when {
                expression {params.Environment == 'Prod'}
            }
            steps {
                input message: 'Confirmation needed for Production deployment', ok: 'Deploy'
                echo "Building Prod stage with confirmation"
            }

        }
    }
}
