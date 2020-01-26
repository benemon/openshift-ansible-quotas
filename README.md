# openshift-ansible-quotas

A role to set default project quotas and limitranges across a list of projects/namespaces in OpenShift.

## Requirements

* Ansible 2.7 or later
* k8s module
* openshift module
* OpenShift oc client installed

## Usage

* Update the `group_vars/all` file with the list of projects to operate against
* Update the `group_vars/all` file with any changes to the default quotas and limitranges specified in `roles/openshift-quotas/defaults/main.yml`
* `ansible-playbook site-install.yml`

## Known Issues and Points of Note

* Won't be able to accurately remove resource requests / limits from multi-container Pods, e.g. Sidecars. Manual intervention will be required for these.
* Doesn't enforce user-level quotas
* "One size doesn't fit all" for either quotas or limit ranges. Whilst the values in this playbook are fairly middle of the road, they may not necessarily apply to your use cases.
* A better and more permenant alternative to using this playbook is to set project quotas and limitranges in the default request template.

## Further Reading

### OpenShift Container Platform 3

* [Quotas](https://docs.openshift.com/container-platform/3.11/admin_guide/quota.html)
* [Limit Ranges](https://docs.openshift.com/container-platform/3.11/admin_guide/limits.html)

### OpenShift Container Platform 4

* [Quotas](https://docs.openshift.com/container-platform/4.3/applications/quotas/quotas-setting-per-project.html)