# EDB User Documentation

This document will cover all the information necessary for users to make use of EDB and its operator on our cluster.

## Installing the Operator

You can find a definition for a namespace-scoped EDB operator in `operations/deployment` - run the following command to install it: `oc apply -f edb-operator-subscription`

If you wish to alter the definition of the subscription object, please **only change the name**. Do not touch the other settings. Most changes are likely to prevent the subscription from installing at all, but changing the `channel` to something other than `stable` may result in what *appears* to be a solid operator, but may result in issues during automatic updates in the future.

If it fails, please check that you have namespace admin rights - edit is not sufficient. You must be an administrator of your namespace. If you do have the correct permissions but it still fails, the issue may be that your namespace doesn't have an operator group yet. Please ping a member of the platform services team on the #edb channel on Rocketchat to find information about how to request that change.

## Installing a Cluster

You can find a template for installing an EDB cluster in `operations/deployment` - run the following command to install it: 
`oc process -f edb-cluster.yaml --param-file=example-cluster.param | oc apply -f -`

The `example-cluster.param` file includes only the minimum number of parameters necessary for the template to function - the rest of the parameters specified in the template would be set as the defaults. You can find a full list of the template's parameters in the template yaml file. Feel free to adjust them as you require. You are likely to want to reduce the CPU requests in accordance with your license. 

You can find a full outline of all of the available options in the Cluster spec (which can be added to the template or can inform your choice to create your own template) [here](https://www.enterprisedb.com/docs/kubernetes/cloud_native_postgresql/api_reference/#clusterspec).

## Creating Backups, Scheduling Backups, and other EDB-related functionality

Please see the [EDB Documentation](https://www.enterprisedb.com/docs/kubernetes/cloud_native_postgresql/backup_recovery/) for details on how to create object definitions and templates for things like backups.
