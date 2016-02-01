.. _setting_up:

Setting Up for Zephyr Development
#################################

Setting up your development environment for Zephyr is done in two steps:

1. Access the code
2. Set up the development environment

Access the Code
***************

Currently, the code is hosted at 01.org and code review is done using Gerrit.
Therefore, a 01.org account is needed to access the code. Follow these steps
to gain access to the code in Gerrit:

#. `Create`_ or `update`_ a `01.org`_ account.

#. Request access by contacting the Zephyr project team.

#. Once access is granted, `access Gerrit`_.

#. Log in using your 01.org account credentials.

.. _Create: https://01.org/user/register

.. _update: https://01.org/user/login

.. _access Gerrit: https://oic-review.01.org/gerrit/

.. _01.org: https://01.org/

Configuring Gerrit to Use SSH
=============================

Gerrit uses SSH to interact with your Git client. A SSH private key
needs to be generated on the development machine with a matching public
key on the Gerrit server.

If you already have a SSH key-pair, skip this section.

As an example, we provide the steps to generate the SSH key-pair on a Linux
environment. Follow the equivalent steps on your OS.

#. Create a key-pair, enter:

   .. code-block:: console

      $ ssh-keygen -t rsa -C "John Doe john.doe@example.com"

   .. note::
      This will ask you for a password to protect the private key as it
      generates a unique key. Please keep this password private, and DO NOT
      enter a blank password.

   The generated key-pair is found in:
   :file:`~/.ssh/id_rsa` and :file:`~/.ssh/id_rsa.pub`.

#. Add the private key in the :file:`id_rsa` file in your key ring:

   .. code-block:: console

      $ ssh-add ~/.ssh/id_rsa

Once the key-pair has been generated, the public key must be added to Gerrit.

Follow these steps to add your public key :file:`id_rsa.pub` to the Gerrit
account:

1. Go to `access Gerrit`_.

2. Click on your account name in the upper right corner.

3. From the pop-up menu, select :guilabel:`Settings`.

4. On the left side menu, click on :guilabel:`SSH Public Keys`.

5. Paste the contents of your public key :file:`~/.id/id_rsa.pub` and click
   :guilabel:`Add key`.

.. note::
   The :file:`id_rsa.pub` file can be opened using any text editor. Ensure
   that all the contents of the file are selected, copied and pasted into the
   :guilabel:`Add SSH key` window in Gerrit.

.. warning::
   Potential Security Risk! Do not copy your private key
   :file:`~/.ssh/id_rsa` Use only the public :file:`~/.id/id_rsa.pub`.

Gerrit Commit Message Hook
==========================

.. include:: ../collaboration/code/gerrit_practices.rst
   :start-line: 42
   :end-line: 49

.. _code_check_out:

Checking Out the Source Code
============================

#. Ensure that SSH has been set up properly. See
   `Configuring Gerrit to Use SSH`_ for details.

#. Clone the repository:

   .. code-block:: console

      $ git clone
      ssh://01ORGUSERNAME@oic-review.01.org:29418/forto-collab zephyr-project

You have successfully checked out a copy of the source code to your local
machine.

.. important::
   Linux users need to download the Zephyr SDK even after successfully
   cloning the source code. The SDK contains packages that are not part of
   the Zephyr Project. See :ref:`zephyr_sdk` for details.

Set Up the Development Environment
**********************************

The Zephyr project supports these operating systems:

* Linux
* Mac OS

Follow the steps appropriate for your development system's
:abbr:`OS (Operating System)`.

Use the following procedures to create a new development environment. Given
that the file hierarchy might change from one release to another, these
instructions could not work properly in an existing development environment.

Perform the steps in the procedures in the order they appear.

.. toctree::
   :maxdepth: 2

   installation_linux.rst
   installation_mac.rst