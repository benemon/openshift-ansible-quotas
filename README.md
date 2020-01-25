# openshift-ansible-quotas

A role to set default project quotas and limitranges across a list of projects/namespaces in OpenShift

## Requirements

* Ansible 2.7 or later
* k8s module
* openshift module
* OpenShift oc client installed

## Usage

* update the `group_vars/all` file with the list of projects to operate against
* update the `group_vars/all` file with any changes to the default quotas and limitranges specified in `roles/openshift-quotas/defaults/main.yml`
* `ansible-playbook site-install.yml`