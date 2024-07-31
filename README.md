# AWS copilot manifests to deploy iloveconference

Deploy nginx, client, and server to a single ECS task running on fargate behind an ALB.

## Install

Host your domain in Route53.

Delete .workspace

Run `copilot app init --domain <domain>` (without www). 
Name the application; e.g., ilc
This creates infrastructure on AWS. 

Run `copilot init`
You want a Load Balanced Web Service. 
Pass in the location of your existing server image.

Delete the <application name> directory that copilot created for you 
and rename the old application directory to your application name.

Change the application name in <application name>/addons/cw-access.yml.
Make all of the necessary changes to <application name>/manifest.yml including updating the ECR locations.

Run `copilot env init` to initialize a `prod` environment

Run `copilot env deploy --name prod` to create more infrastructure.

Run `copilot secret init` to add the following secrets
- UPSTASH\_REDIS\_REST\_URL
- UPSTASH\_REDIS\_REST\_TOKEN
- OPENAI\_API\_KEY
- PINECONE\_API\_KEY
- PINECONE\_ENV
- VOYAGE\_API\_KEY (not currently used)
- COHERE\_API\_KEY (not currently used)

## Usage

Update <application name>/manifest.yml with the latest image tags for client and server from the github actions output.

The run `copilot deploy`

If you need to update a secret, rerun `copilot secret init` with the `--overwrite` parameter.
