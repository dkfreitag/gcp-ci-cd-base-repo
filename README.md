# GCP CI/CD Base Repo

This is the base code for a Flask app inside a Docker container that can be deployed via Cloud Build in GCP with continuous integration/continuous deployment.

You'll need to link the GitHub repo to Cloud Build and authenticate to allow Cloud Build to detect new commits to the repo.
Once configured, simply push a commit to this git repo, and a Cloud Build trigger will build a new Docker image using the most up-to-date source.
The resulting container is hosted in Artifact Registry and is continuously deployed as a serverless service via Cloud Run.
As soon as a new container is available, the Cloud Run service switches traffic to be served by the new container.

### Setup Steps:
- Connect your GitHub repo to Cloud Build: https://cloud.google.com/build/docs/automating-builds/github/connect-repo-github
- In Cloud Run, create a new service.
- Choose `Continuously deploy new revisions from a source repository` and choose your repo.

### Cleanup:
- Disconnect the repo in Cloud Build
- Delete the Cloud Build trigger
- Delete all containers from Artifact Registry
- Delete the service in Cloud Run
