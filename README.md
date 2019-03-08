# Java servlet on a dockerized Alpine Linux image, hosted on AWS EC2 instance.

prerequisite:

ansible

assumptions:

- AWS credentials are configured on the machine running the ansible playbook.
- S3 bucket and dynamo db tables are created beforehand using terraform/common/* to store terraform state file of EC2 instance.

facts:

- for project purposes, apro is used as the repository to download terraform. it can be replaced by <https://releases.hashicorp.com/terraform/0.11.11/terraform_0.11.11_linux_amd64.zip> for common use.

run:

ansible-playbook playbooks/mmk_java_server/runall.yml -i inventory/deploy_instances --private-key secrets/mmk-java-servlet-key-pair.pem -e "TF_VAR_AWS_PROFILE=<<"aws profile name">> TF_VAR_AWS_REGION=<<"aws region">>"

usage:

Java servlet is exposed on the local port which is exposed during the run.

root context: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/>

get header info: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/echoHeader>

custom http get: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/echoGet?name=Peter,Udayan,Manju>

reference:

<https://www.codeproject.com/Tips/1040097/Create-a-Simple-Web-Server-in-Java-HTTP-Server>
