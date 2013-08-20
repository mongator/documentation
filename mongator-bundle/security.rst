Security
========

The MongatorBundle comes with the *MongatorUserProvider* provider to integrate
your Mongator's documents with the Symfony2 security layer.

.. code-block:: yaml

    services:
        security.provider.mongator:
            class: Mongator\MongatorBundle\Security\MongatorUserProvider
            arguments: [@mongator, Model\User, username]

    security:
        providers:
            mongator:
                id: security.provider.mongator
