Kpt playground
===

# PKG User

Get

```
PKG=https://github.com/kubernetes/examples/staging/cockroachdb
DIR=cockroachdb
kpt pkg get ${PKG} ${DIR}
```

Set

```
DIR=cockroachdb
kpt cfg create-setter ${DIR} replicas 3 --field "spec.replicas"

kpt cfg list-setters ${DIR} --set-by david --description "Increase replicas to 5"
    NAME     VALUE   SET BY   DESCRIPTION   COUNT
  replicas   3                              1

kpt cfg set ${DIR} replicas 5
set 1 fields
```

Apply

```
kpt live init sleepybox # init configmap
kpt live diff
```

Update

```
kpt pkg update sleepybox@0.0.2 --strategy=resource-merge
```

Function

```
kpt fn run --image gcr.io/kpt-functions/label-namespace . -- label_name=color label_value=orange
```

---

# PKG Provider

Substitution

```
kpt cfg create-subst sleepybox image-value --field-value alpine:3.12.0 --pattern alpine:\${TAG_SETTER}
unable to find setter with name TAG_SETTER, creating new setter with value 3.12.0

kpt cfg set sleepybox TAG_SETTER 1.8.1
```

Blueprint
```
kpt pkg get https://github.com/GoogleContainerTools/kpt.git/package-examples/mysql-kustomize mysql
```
