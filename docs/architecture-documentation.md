# EDB Architecture Doc

This document will cover the architectural decisions about how we have chosen to implement EDB and its operator on our cluster.

Each team create their own instance of the operator on their own namespace. This requires that the CRDs be in place on the cluster already (cluster-admin required) and that the namespace have an operator-group already in place for the operator to use (bcdevops-admin required). Once each of these requirements are in place, the team can then create a subscription object in order to create the namespace-scoped operator.

In order to get the CRDs onto the cluster, CCM will create a namespace called `edb-operator` and install the first instance of the operator on the cluster using cluster-admin privileges. This operator will not actually do anything - it will not control any EDB clusters, it will not perform backups, it will do nothing. It will be namespace-scoped in order to ensure it cannot accidentally cause problems for other namespaces. This instance of the operator exists solely to create the necessary CRDs and to ensure that they remain up-to-date.

Because end-users don't have the rights required to create the operator group in their namespace, this is a task that will require some additional action on the part of the platform group. This will be added to the project provisioner. Currently, a hard-coded list of projects requiring the operator-group object defines which projects get the object.

## What About CRD Compatibility?

Teams must allow automatic operator updates. When the operator living in `edb-operator` gets updated automatically, the CRDs will update as required. The namespace-scoped operators will then be able to update as well. There will, therefore, be a very small window of time in which the namespace-scoped operators will be a version behind the CRDs. However, EDB (the company) has provided assurance of compatibility between immediately adjacent versions of the operator, so this window is not a concern.

Note that this is about updating the version of the *operator*, not the database version of the Postgres cluster. Those are totally different things, the latter of which is not automatic (and is controlled by the teams).
