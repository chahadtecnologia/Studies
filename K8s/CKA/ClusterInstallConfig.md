# Cluster Architecture, Installation and Configuration

## RBAC High-Level Overview

- Establishing a system for users with different roles to access a set of Kubernetes resources.
- Controlling processes running in a Pod and the operations they can perform via the Kubernetes API.
- Limiting the visibility of certain resources per namespace.

RBAC consist of three key building blocks. Together, they connect API primitives and their allowed operations to the so-called subject, wich is a user, a group, or a ServiceAccount.

- **Subject (Users, Groups, ServiceAccounts)** = The user or process that wants to access a resource.
- **Resource (ConfigMap, Deployment, Node, etc)** = The Kubernetes API resource type (e.g., a Deployment or node)
- **Verb (Create, List, Watch, Delete, etc)** = The operation that can be executed on the resource (e.g, creating a Pod or deleting a Service).

## Creating a Subject

In the context of RBAC, you can use a user account, service account, or a group as a subject. Users and groups are not stored in *etcd*, the Kubernetes database, and are meant for processes running outside of the cluster. Service accounts exists as objects in Kubernetes and are used by processes running inside of the cluster. 

## Authentication strategies for managing RBAC subjects

- **x.509 client certificate** = Uses an OpenSSL client certificate to authenticate.
- **Basic authentication** = Uses username and password to authenticate.
- **Bearer tokens** = Uses OpenID (a flavor of OAuth2) or webhooks as a way to authenticate.

## Understanding RBAC API Primitives

- **Role** = The Role API primitive declares the API resources and their operations this rule should operate on.

- **RoleBinding** = The RoleBinding API primitive binds the Role object to the subject(s). It is the glue for making the rules active.


Example:

**[ Service, Pod, Node... ] <----- Role [ get, list... ] <----- RoleBinding -----> [ User, Group, ServiceAccount ]**

## Default User-Facing Roles

- **cluster-admin** = Allows read and write access to resources across all namespaces.
- **admin** = Allows read and write access to resources in namespace including Roles and RoleBindings.
- **edit** = Allows read and write access to resources in namespace except Roles and RoleBindings. Provides access to Secrets.
- **view** = Allows read-only access to resources in namespace except Roles, RoleBindings, and Secrets.