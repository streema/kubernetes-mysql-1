# kubernetes-mysql

#### Build an EBS volume in AWS

`aws ec2 create-volume --availability-zone us-west-2a --size 30 --volume-type gp2`

* Insert the volume id of your newly created ebs volume into your mysql.yaml

#### Create k8s secret

##### create password file
`echo This-is-a-password > password`

##### create k8s secret for root password
`kubectl -n mysql create secret generic db-password --from-file=./password`


#### Create mysql pod

`kubectl create -f mysql.yaml`

Make sure mysql pod is running

`kubectl get pod mysql`

#### Create mysql service

`kubectl create -f mysql-service.yaml`

Get internal Cluster-IP for the mysql service

`kubectl get service mysql`
