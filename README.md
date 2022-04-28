# Infrastructure Playbooks

Setup Playbooks to provision cloud infrastructure.

## aws_infra.yml

- install the Execution Environment [ee-ansible-ssa](https://quay.io/repository/redhat_emp1/ee-ansible-ssa) from Quay - you will need an Red Hat employee account to sign in

```bash
podman login quay.io
podman pull quay.io/redhat_emp1/ee-ansible-ssa
```

- export your AWS credentials as environment variables:

```bash
AWS_SECRET_ACCESS_KEY=
AWS_ACCESS_KEY_ID=
```

Ideally you create your AWS account by using the "Open Environment" in [RHPDS](https://rhpds.redhat.com/service/explorer).

- define SSH key pair

- update [group_vars/all/main.yml](group_vars/all/main.yml) with your settings

- run the playbook with [ansible-navigator](https://ansible-navigator.readthedocs.io/en/latest/)

```bash
ansible-navigator run aws-infra.yml
```

### Remove

The [instance role](https://gitlab.com/ansible-ssa/role-instance) this Playbook is using, does also support removal by using the `remove=true` variable:

```bash
ansible-navigator run aws-infra.yml -e remove=true
```
