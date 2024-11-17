Azure resources
===============

Most of our critical services (i.e., ones that need to be reliable) run on Azure.

This includes:

* Vaultwarden_
* Mattermost_
* `Our website`_

.. _Vaultwarden: https://vault.hackerspace.gent
.. _Mattermost: https://chat.hackerspace.gent
.. _`Our Website`: https://hackerspace.gent


Accessing VMs
=============

Access is provided through the Azure CLI. You will need to `install it`_ before you continue.
Once you have the Azure CLI installed, login via ``az login`` and then install the extension using

.. code-block:: shell
  $ az extension add --name ssh

You can then list available VMs (note that you may not have access to all listed machines)

.. code-block:: shell
  $ az vm list  | jq '.[] | {resourceGroup, name}'

or login to a specific VM using

.. code-block:: shell
  az ssh vm --resource-group otherservers --name generic-server

.. _`install it`: https://learn.microsoft.com/en-us/cli/azure/install-azure-cli
