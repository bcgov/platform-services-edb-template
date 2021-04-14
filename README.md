# platform-services-edb-template

This repo contains documentation and templates for the use of EDB and its operator.

## End Users

You can find user documentation and the service definition in the `docs` folder.

There is a community of other users availble on the `#edb` channel on [RocketChat](https://chat.developer.gov.bc.ca). You may also find it useful to jump onto the `#patroni` channel as well, in order to make use of that community's larger size for more general HA Postgres support.

EDB offers [extensive documentation](https://www.enterprisedb.com/docs/kubernetes/cloud_native_postgresql/) on the use of the operator - much of the relevant information (including instructions on how to create clusters, backups and other things with the operator) can be found there. Since this is a licensed product, all users should also have access to EDB's [Support Portal](https://support.enterprisedb.com/support/s/).

There are also templates for users to support installation of the operator in `operations/deployment`. However, it is highly recommended that you read `docs/user-documentation.md` before you attempt to use them.

## Platform Services Team

You can find operational and architectural documentation in the `docs` folder.

Templates for installing the CRDs will be controlled by CCM and are contained in the CRM repo rather than being here.
