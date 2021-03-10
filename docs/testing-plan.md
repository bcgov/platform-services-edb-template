# Testing Plan

## Can we even install it?

The hope is that we can make it so that the platform team installs the CRDs on the cluster in an automated manner, and then the teams can use OperatorHub to install the operator itself on their own namespace. However, this may not work because the OperatorHub installation includes the CRDs (which require cluster-admin) so I will test to see 
