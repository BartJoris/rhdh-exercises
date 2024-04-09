# Lab Preparation

## Start OCP

request a "Red Hat OpenShift Container Platform Cluster" instance from demo.redhat.com

## Install cert-manager operator

```sh
oc apply -f ./cert-manager-operator.yaml
```

## Install gitlab operator

```sh
oc create namespace gitlab-system
oc apply -f https://gitlab.com/api/v4/projects/18899486/packages/generic/gitlab-operator/0.30.1/gitlab-operator-openshift-0.30.1.yaml
```

## Deploy gitlab

```sh
export basedomain=$(oc get ingresscontroller -n openshift-ingress-operator default -o jsonpath='{.status.domain}')
envsubst < ./gitlab.yaml | oc apply -f -
```

git lab is not accessible with user `root/<password in "gitlab-gitlab-initial-root-password" secret>`

create two groups

- team-a
- team-b

create two users

- user1
- user2

ensure user1 belongs to team-a and user2 belongs to team-b

create a repo called `sample-app` udner `team-a` add the `catalog-info.yaml` at the root of the repo.

## Install rhdh operator

```sh
oc apply -f ./rhdh-operator.yaml
```

## Install rhdh instance

```sh
oc apply -f ./rhdh-instance.yaml
```