# AWS copilot manifests to deploy iloveconference

Deploy nginx, client, and server to a single ECS task running on fargate behind an ALB.

## Usage

Update client-server/manifest.yml with the latest image tags for client and server from the github actions output.

The run `copilot deploy`

