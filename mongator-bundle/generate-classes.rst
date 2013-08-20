Generate Classes
================

The config classes are defined in the application and bundles config directories,
and they are defined in YAML_.

.. code-block:: yaml

    app/config/mongator/*.yml
    *Bundle/Resources/config/mongator/*.yml

You must to use the standard namespace *Model* in the classes, thus the bundles will be
reusable and coherent.

You don't need to use bundle namespace in your application classes:

.. code-block:: yaml

    # app/config/mongator/schema.yml
    Model\Article:
        fields:
            title:   string
            content: string

In the bundles is necessary to use the bundle name to separate the classes by bundle:

.. code-block:: yaml

    # src/Mongator/MongatorUserBundle/Resources/config/mongator/schema.yml
    Model\MongatorUserBundle\User:
        fields:
            username: string
            password: string

The classes are generated in the *src/Model* directory, and the bundle classes extend of
a bundle class before of the base class to be able to custom them in the bundles.

.. code-block:: yaml

    # application class
    Model\Article:
        Model\Base\Article

    # bundle class
    Model\MongatorUserBundle\User:
        Mongator\MongatorUserBundle\Model\User:
            Model\MongatorUserBundle\Base\User

To generate the classes is used the *mongator:generate* command:

.. code-block:: bash

    php app/console mongator:generate

.. _YAML: http://www.yaml.org
