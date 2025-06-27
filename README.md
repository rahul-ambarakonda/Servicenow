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

## GitHub to Jenkins CI/CD Integration

To trigger Jenkins jobs from GitHub (and optionally connect ServiceNow):

### 1. Jenkins Setup
- Install the “GitHub Integration” and “GitHub” plugins in Jenkins.
- Create a Jenkins job (Pipeline or Multibranch Pipeline) connected to your GitHub repo.
- In job configuration, under “Build Triggers,” check “GitHub hook trigger for GITScm polling.”

### 2. GitHub Webhook
- Go to your repository → Settings → Webhooks → Add webhook.
- Payload URL: `http://<jenkins-server>/github-webhook/`
- Content type: `application/json`
- Select events (e.g., push, pull request).
- Save.

### 3. Test
- Make a commit or PR in GitHub. Jenkins should trigger the job automatically.

### Optional: ServiceNow to Jenkins
- Use IntegrationHub (Flow Designer) or Scripted REST API in ServiceNow to send an HTTP POST to Jenkins’ job URL when a ServiceNow event occurs.
- Jenkins can also update ServiceNow via REST API after deployment or testing.

## Notes
- The Jenkinsfile uses a `curl` command to upload the update set. You may need to adjust the API endpoint or authentication for your instance.
- Add automated tests as needed.
