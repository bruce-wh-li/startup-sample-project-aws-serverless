# Serverless Architecture

![Serverless Architecture](./images/serverless-architecture.png)

# startup-sample-project-aws-serverless
Lambda serverless app meant to accelerate teams onboarding to the BC Gov SEA AWS space.

## Setup
- Fork this repo
- Enable github actions
#### Github Secrets
you'll need to add two github secrets:
  - `LICENCEPLATE` is the 6 character licensecho "x"e plate associated with your project set e.g. `abc123`
  - `TFC_TEAM_TOKEN` is the token used to access the terraform cloud runner.
  - To access the TFC_Team_Token: Log to AWS> Search for Parameter Store > the key is under /octk/tfc/team_token
  - Once the app has been built, you should be able to log into AWS with your IDIR account (2FA). Once in AWS search for Cloudfront and then click on Distributions (If you can not see it click the hamburger on the top left corner). The Distributions dashboard shows the Domain name, you can use that domain name to interact with you app.


#### Pipeline
The github actions will trigger on a pull request creation and merge.
- Creating a pull request will run a `terraform plan` and outline everything that will be deployed into your AWS accounts, but will not create anything.
- Merging into `main` will run a `terraform apply` and your AWS assets will be deployed into your `dev` and `sandbox` accounts.

NOTE: make sure you are creating pull requests/ merging within your fork

#### Security 
To adopt checkov of bridgecrew.io, a static scanning tool for IaC and SCA (Software Composition Analysis), in CI/CD pipeline to automatically 
detect the misconfiguration in IaC file and  Common Vulnerabilities and Exposures (CVEs) in the open source packages and images in the provision. 

 - One github action workflow added for SCA and IaC scanning : Checkov.yml will be triggered when there is a git push on `main` branch.
 - Free Tier has reduced features and 50 resource limitation 
 - VCS Integration for additional features


#### Testing
For how to use the test associated to this project, please check the README file under `functional-tests`


## Testing Thanks

Thanks to BrowserStack for Testing Tool support via OpenSource Licensing ![BrowserStack](docs/images/browserstack-logo-white-small.png)

[![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/bruce-wh-li/startup-sample-project-aws-serverless/cis_aws)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=bruce-wh-li%2Fstartup-sample-project-aws-serverless&benchmark=CIS+AWS+V1.2)[![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/bruce-wh-li/startup-sample-project-aws-serverless/cis_aws_13)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=bruce-wh-li%2Fstartup-sample-project-aws-serverless&benchmark=CIS+AWS+V1.3)[![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/bruce-wh-li/startup-sample-project-aws-serverless/iso)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=bruce-wh-li%2Fstartup-sample-project-aws-serverless&benchmark=ISO27001)
