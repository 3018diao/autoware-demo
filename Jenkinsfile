pipeline {
    agent any

    parameters {
        choice(name: 'CATALOG', choices: ['Vehicle1', 'Vehicle2'], description: 'Select the vehicle catalog to be evaluated')
        string(name: 'SUITE', defaultValue: 'All', description: 'Test suite to run')
        choice(name: 'SCM_TYPE', choices: ['Git', 'Web.Auto', 'Reuse build artifacts'], description: 'Select the management method of the source code')
        string(name: 'GIT_BRANCH_TAG_COMMIT', defaultValue: '', description: 'Git branch, tag, or commit ID (if SCM Type is Git)')
        string(name: 'SOURCE_ID', defaultValue: '', description: 'SourceID for Web.Auto (if SCM Type is Web.Auto)')
        string(name: 'JOB_ID', defaultValue: '', description: 'Job ID for reusing build artifacts (if SCM Type is Reuse build artifacts)')
        booleanParam(name: 'RELEASE', defaultValue: false, description: 'Enable release')
        booleanParam(name: 'PARTIAL_RELEASE', defaultValue: false, description: 'Enable partial release')
        booleanParam(name: 'CLEAN_BUILD', defaultValue: false, description: 'Enable clean build')
        booleanParam(name: 'DEBUG_BUILD', defaultValue: false, description: 'Enable debug build')
        booleanParam(name: 'SKIP_TEST', defaultValue: false, description: 'Skip the test')
        string(name: 'MAX_TEST_RETRIES', defaultValue: '0', description: 'Number of times to retry on test failure')
        string(name: 'DESCRIPTION', defaultValue: '', description: 'Description for the test')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    if (params.SCM_TYPE == 'Git') {
                        checkout scm: [ $class: 'GitSCM', branches: [[name: params.GIT_BRANCH_TAG_COMMIT]], userRemoteConfigs: [[url: '<GIT_REPO_URL>']]]
                    } else {
                        echo "Non-Git SCM types not implemented in this example"
                    }
                }
            }
        }

        stage('Build') {
            when {
                not {
                    expression { params.SKIP_TEST }
                }
            }
            steps {
                script {
                    if (params.CLEAN_BUILD) {
                        // Add commands for clean build here
                        echo "Performing clean build..."
                    }
                    if (params.DEBUG_BUILD) {
                        // Add commands for debug build here
                        echo "Performing debug build..."
                    }
                    // Add your build commands here
                    echo "Building the project..."
                }
            }
        }

        stage('Test') {
            when {
                not {
                    expression { params.SKIP_TEST }
                }
            }
            steps {
                script {
                    // Add commands to run tests here
                    // Use params.SUITE to select the test suite
                    echo "Running test suite ${params.SUITE}..."
                }
            }
        }

        stage('Release') {
            when {
                expression { params.RELEASE }
            }
            steps {
                script {
                    // Add commands for release here
                    if (params.PARTIAL_RELEASE) {
                        echo "Performing partial release..."
                    } else {
                        echo "Performing full release..."
                    }
                }
            }
        }
    }

    post {
        always {
            // Add steps to clean up workspace, notify users, etc.
            echo "Build completed"
        }
    }
}
