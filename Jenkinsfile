pipeline {
    agent any
    parameters {
        choice(name: 'TEST_SUITE_TYPE', choices: ['planning_sim', 'planning_sim_v2', 'log_sim', 'localization', 'ndt_convergence', 'obstacle_detection', 'perception', 'performance_diag', 'obstacle_segmentation', 'yabloc', 'eagleye'], description: 'Select a scenario type for the test suite.')
        string(name: 'TEST_SUITE_NAME', defaultValue: '', description: 'Enter the name of the test suite.')
        string(name: 'SCENARIO_VERSION', defaultValue: 'Latest', description: 'Specify the version of the scenario to add to the test suite.')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Execute Build'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Execute Unit Test'
            }
        }
        stage('Simlation Test') {
            steps {
                echo 'Execute Simlation Test'
            }
        }
    }
}
