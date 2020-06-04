Kpt playground
===

# Get

```
PKG=https://github.com/kubernetes/examples/staging/cockroachdb
DIR=cockroachdb
kpt pkg get ${PKG} ${DIR}
```

# Set

```
DIR=cockroachdb
kpt cfg create-setter ${DIR} replicas 3 --field "spec.replicas"

kpt cfg list-setters ${DIR} --set-by david --description "Increase replicas to 5"
    NAME     VALUE   SET BY   DESCRIPTION   COUNT
  replicas   3                              1

kpt cfg set ${DIR} replicas 5
set 1 fields
```
