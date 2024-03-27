## Steps to run the KMS PoC on OpenShift:
etcd encryption of secrets and configmaps with AWS KMS provider

1. Create an AWS cluster using regular IPI method
(optional) For convenience, one can use: https://github.com/swghosh/raining-openshift-clusters/blob/main/create-cluster-aws.sh
- The OpenShift release image I tested on was
export OPENSHIFT_INSTALL_RELEASE_IMAGE_OVERRIDE=quay.io/openshift-release-dev/ocp-release:4.16.0-ec.1-x86_64
https://amd64.ocp.releases.ci.openshift.org/releasestream/4-dev-preview/release/4.16.0-ec.1

- Please refrain from using an AWS cluster provisioned by cluster-bot as the root aws-creds in the CI cluster created by cluster-bot lack permissions to create a KMS instance in AWS!
Used our openshift-dev aws credentials from local to create cluster and it works fine, has the permissions available to create KMS instance

2. Once cluster is up and IPI install stages, bootstrapping, etc. have finished
Clone the PR branch in https://github.com/openshift/cluster-kube-apiserver-operator/pull/1625 locally
- Run `bash hack-kms/run-operator-locally.sh`