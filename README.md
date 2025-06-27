# Demo CI/CD App for ServiceNow

This repository contains a simple ServiceNow application and a Jenkins pipeline for CI/CD testing.

## Files
- `demo_ci_cd_update_set.xml`: Update set to import into your ServiceNow developer instance.
- `Jenkinsfile`: Example Jenkins pipeline to automate update set import.

## Steps
1. Import `demo_ci_cd_update_set.xml` into your ServiceNow instance (System Update Sets > Retrieved Update Sets > Import Update Set from XML).
2. Preview and commit the update set.
3. Configure Jenkins with your ServiceNow instance credentials.
4. Run the Jenkins pipeline to automate update set import.

## Notes
- The Jenkinsfile uses a `curl` command to upload the update set. You may need to adjust the API endpoint or authentication for your instance.
- Add automated tests as needed.
