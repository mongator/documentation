Security
========

The MongatorBundle comes with the *MongatorUserProvider* provider to integrate
your Mongator's documents with the Symfony2 security layer.

.. code-block:: yaml

    services:
        security.provider.mandango:
            class: Mongator\MongatorBundle\Security\MongatorUserProvider
            arguments: [@mandango, Model\User, username]

    security:
        providers:
            mandango:
                id: security.provider.mandango
