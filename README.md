# Java servlet on a dockerized Alpine Linux image, hosted on AWS EC2 instance.

prerequisite:

ansible

assumptions:

- AWS credentials are configured on the machine running the ansible playbook.
- S3 bucket and dynamo db are created beforehand. terraform files and their state files are stored under terraform/common

run:

ansible-playbook playbooks/mmk_java_server/runall.yml -i inventory/deploy_instances --private-key secrets/mmk-java-servlet-key-pair.pem -e "TF_VAR_AWS_PROFILE=saml TF_VAR_AWS_REGION=ap-southeast-2"

usage:

Java servlet is exposed on the local port which is exposed during the run.

root context: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/>

get header info: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/echoHeader>

custom http get: <http://mmk-private-hosted-java-server.nbn-aws-learning.local.apps.sandpit.nbn-aws.local:9020/echoGet?name=Peter,Udayan,Manju>

reference:

<https://www.codeproject.com/Tips/1040097/Create-a-Simple-Web-Server-in-Java-HTTP-Server>
