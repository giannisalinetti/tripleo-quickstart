# Configure a static inventory and SSH config to access nodes

The `tripleo-inventory` role generates a static inventory and SSH config,
based on a deployment mode and a type of undercloud.

## Openstack inventory

When cluster nodes are pre-provisioned and hosted on an OpenStack host cloud,
use the `inventory: openstack` mode. Fetched data from the dynamic
`shade-inventory` will be filtered by the `clusterid`, if defined, and
by node types, like overcloud/undercloud/bastion. Then the filtered data is
stored into the static inventory and SSH config is generated to access
overcloud nodes via a bastion, which is the undercloud node as well.

The following variables should be customized to match the host OpenStack cloud
configuration:

* `clusterid`: -- an optional Nova servers' metadata parameter to identify
  your environment VMs.
* `openstack_private_network_name`:<'private'> -- defines a private network
  name used as an admin/control network. Ansible and SSH users will use that
  network when connecting to the inventory nodes via the undercloud/bastion.
* `os_username`: -- credentials to connect the OpenStack cloud hosting
  your pre-provisioned Nova servers.
* `os_password`: -- credentials to connect the host OpenStack cloud.
* `os_project_name`: -- credentials to connect the host OpenStack cloud.
* `os_tenant_name`: -- credentials to connect the host OpenStack cloud.
* `os_auth_url`: -- credentials to connect the host OpenStack cloud.
* `cloud_name`: -- credentials to connect the host OpenStack cloud.
* `os_identity_api_version`: -- credentials to connect to the OpenStack cloud.
* `os_region_name`: -- credentials to connect to the OpenStack cloud.

TODO(bogdando) document remaining modes 'all', 'undercloud'.
