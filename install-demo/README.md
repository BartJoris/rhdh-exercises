# Configure lab prep with Ansible

This will perform the following:
- Install pre-requisites on local machine
- Install cert-manager on OpenShift
- Install GitLab
- Configure Gitlab with example users and projects
- Install Developer Hub
- Configure auth provider GitLab for Developer Hub

```sh
git clone git@github.com:BartJoris/rhdh-exercises.git
cd rhdh-exercises/install-demo
cp example_vars.yaml vars.yaml
```
Modify the vars file if needed

Run the ansible playbook:
```sh
ansible-playbook install.yaml -vv
```
