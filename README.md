# Infrastructure Playbooks

Setup Playbooks to provision cloud infrastructure.

## AWS

- install the Execution Environment [ee-ansible-ssa](https://quay.io/repository/redhat_emp1/ee-ansible-ssa) from Quay - you will need an Red Hat employee account to sign in

```bash
podman login quay.io
podman pull quay.io/redhat_emp1/ee-ansible-ssa
```

- export your AWS credentials as environment variables:

```bash
export AWS_SECRET_ACCESS_KEY=<secret-access-key>
export AWS_ACCESS_KEY_ID=<access-key-id>
```

Ideally you create your AWS account by using the "Open Environment" in [RHPDS](https://rhpds.redhat.com/service/explorer).

- update [group_vars/all/main.yml](group_vars/all/main.yml) with your settings

- run the playbook with [ansible-navigator](https://ansible-navigator.readthedocs.io/en/latest/)

```bash
ansible-navigator run cloud-infra.yml
```

## Azure

- install the Execution Environment [ee-ansible-ssa](https://quay.io/repository/redhat_emp1/ee-ansible-ssa) from Quay - you will need an Red Hat employee account to sign in

```bash
podman login quay.io
podman pull quay.io/redhat_emp1/ee-ansible-ssa
```

- export your Azure credentials as environment variables:

```bash
export AZURE_SECRET=<your Azure secret>
export AZURE_CLIENT_ID=<your Azure client ID>
export AZURE_SUBSCRIPTION_ID=<your Azure subscription ID>
export AZURE_TENANT=<your Azure tenant ID>
```

Ideally you create your Azure account by using the "Open Environment" in [RHPDS](https://rhpds.redhat.com/service/explorer).

- update [group_vars/all/main.yml](group_vars/all/main.yml) with your settings

- run the playbook with [ansible-navigator](https://ansible-navigator.readthedocs.io/en/latest/)

```bash
ansible-navigator run cloud-infra.yml
```

## Remove instances

The [instance role](https://gitlab.com/ansible-ssa/role-instance) this Playbook is using, does also support removal by using the `remove=true` variable:

```bash
ansible-navigator run cloud-infra.yml -e remove=true
```
