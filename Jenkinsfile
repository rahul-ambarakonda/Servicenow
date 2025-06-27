pipeline {
    agent any
    environment {
        SERVICENOW_INSTANCE = credentials('servicenow-instance-url')
        SERVICENOW_USER = credentials('servicenow-username')
        SERVICENOW_PASS = credentials('servicenow-password')
    }
    stages {
        stage('Import Update Set') {
            steps {
                echo 'Importing update set to ServiceNow...'
                // Example: Use REST API to import update set
                sh '''
                curl -u "$SERVICENOW_USER:$SERVICENOW_PASS" \
                  -F "uploadFile=@demo_ci_cd_update_set.xml" \
                  "$SERVICENOW_INSTANCE/api/now/table/sys_update_set"
                '''
            }
        }
        stage('Preview & Commit') {
            steps {
                echo 'Manual step: Preview and commit the update set in ServiceNow UI.'
            }
        }
        stage('Test Application') {
            steps {
                echo 'Add automated tests here if available.'
            }
        }
    }
}
