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
-------------

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

Managing permissions
--------------------

.. note::
   This is a board-level function.

The entra console is available at https://entra.microsoft.com/

Board members should simply be added to the Board group; this grants all of the necessary permissions (i.e., *everything*).

In general, the permission flow is:

* Users are assigned to groups
* Groups are granted permissions on one or more objects


