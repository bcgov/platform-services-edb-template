# platform-services-edb-template

This repo contains documentation and templates for the use of EDB and its operator.

## End Users

You can find user documentation and the service definition in the `docs` folder.

There will also be templates for users to support installation of the operator in `operations/deployment`. However, it is highly recommended that you read `docs/user-documentation.md` before you attempt to use them.

## Platform Services Team

You can find operational and architectural documentation in the `docs` folder.

Templates for installing the CRDs will be controlled by CCM and are contained in the CRM repo rather than being here.

oc process -f permissive-nsp.yaml -p NAMESPACE=caggles-test | oc apply -f -
