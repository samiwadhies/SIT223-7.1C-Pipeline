pipeline {
    agent any
    triggers {
        // Check GitHub for new commits every 2 minutes
        pollSCM('H/2 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Task: compile the source code and package it into a build artefact (e.g. a JAR or zip).'
                echo 'Tool: Maven (alternatives: Gradle, npm)'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Task: run unit tests to check each function works, then integration tests to check components work together.'
                echo 'Tools: JUnit (unit tests), Selenium / Postman (integration tests)'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Task: analyse the code against industry coding standards (bugs, code smells, duplication, coverage).'
                echo 'Tool: SonarQube (with the SonarQube Scanner for Jenkins plugin)'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Task: scan the code and its dependencies for known vulnerabilities.'
                echo 'Tools: Snyk / OWASP Dependency-Check (dependencies), npm audit'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Task: deploy the build artefact to a staging server that mirrors production.'
                echo 'Tool: AWS CodeDeploy to an AWS EC2 staging instance (alternative: Ansible)'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Task: run integration and smoke tests against the staging environment.'
                echo 'Tools: Selenium / Postman (Newman) against the staging URL'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Task: deploy the tested artefact to the production server.'
                echo 'Tool: AWS CodeDeploy to an AWS EC2 production instance'
            }
        }
    }
    post {
        success { echo 'Pipeline completed successfully.' }
        failure { echo 'Pipeline failed - check the stage logs.' }
    }
}
