# openshift-ansible-quotas

A set of roles for assisting with capacity management in OpenShift.

### openshift-quotas

A role to set default project quotas and limitranges across a list of projects/namespaces in OpenShift.

### openshift-idling

A role to idle all deployments across a list of projects/namespaces in OpenShift.

## Requirements

* Ansible 2.7 or later
* k8s module
* openshift module
* OpenShift oc client installed

## Usage

Each 'host' in the context of this role is an alias to `localhost`. This allows us to configure different groups of projects to target based on a host alias. In the examples provided, the host `cs123` is an alias to localhost which operates on an OpenShift project called `test1`.

By comparison, the host `cs456` is also an alias to localhost, but it operates on OpenShift projects `test2` and `test3`.

Finally, `all-classes` represents a combined list of all projects in the OpenShift cluster.

### openshift-quotas

* Update the `host_vars/*hostname*.yml` file with the list of projects to operate against
* Update the `host_vars/*hostname*.yml` file with any changes to the default quotas and limitranges specified in `roles/openshift-quotas/defaults/main.yml`
* `ansible-playbook site-install.yml -t quotas`

### openshift-idling

* Update the `host_vars/*hostname*.yml` file with the list of projects to operate against
* `ansible-playbook site-install.yml -t idling`

## Known Issues and Points of Note

* Test execution against a small subset of representative projects first
* Won't be able to accurately remove resource requests / limits from multi-container Pods, e.g. Sidecars. Manual intervention will be required for these.
* Doesn't enforce user-level quotas
* "One size doesn't fit all" for either quotas or limit ranges. Whilst the values in this playbook are fairly middle of the road, they may not necessarily apply to your use cases.
* A better and more permenant alternative to using `openshift-quotas` is to set project quotas and limitranges in the default request template.
* Don't run both roles in conjunction with each other. Here be dragons etc etc.

## Further Reading

### OpenShift Container Platform 3

* [Quotas](https://docs.openshift.com/container-platform/3.11/admin_guide/quota.html)
* [Limit Ranges](https://docs.openshift.com/container-platform/3.11/admin_guide/limits.html)
* [Idling](https://docs.openshift.com/container-platform/3.11/admin_guide/idling_applications.html)

### OpenShift Container Platform 4

* [Quotas](https://docs.openshift.com/container-platform/4.3/applications/quotas/quotas-setting-per-project.html)
* [Idling](https://docs.openshift.com/container-platform/4.3/applications/idling-applications.html)
