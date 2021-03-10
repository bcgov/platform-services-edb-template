# EDB Architecture Doc

This document will cover the architectural decisions about how we have chosen to implement EDB and its operator on our cluster.

## The Plan

The platform team will install the CRDs using CRM, and then the users will be able to install the operator as they wish on their local namespace using the subscription object to interact with the OperatorHub.
