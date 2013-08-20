Introduction
============

The MongatorBundle is the bundle to use Mongator with Symfony2_.

Installation
------------

Add Mongator and Mondator to your vendors:

.. code-block:: bash

    git submodule add git://github.com/mandango/mandango vendor/mandango
    git submodule add git://github.com/mandango/mondator vendor/mondator

Add the MongatorBundle:

.. code-block:: bash

    git submodule add git://github.com/mandango/MongatorBundle vendor/bundles/Mongator/MongatorBundle

Add all of them and the Model namespace to your autoload::

    // app/autoload.php
    $loader->registerNamespaces(array(
        // ...
        'Mongator\MongatorBundle' => __DIR__.'/../vendor/bundles',
        'Mongator\Mondator'       => __DIR__.'/../vendor/mondator/src',
        'Mongator'                => __DIR__.'/../vendor/mandango/src',
        'Model'                   => __DIR__.'/../src/',
        // ...
    ));

Add the MongatorBundle to your application kernel::

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new Mongator\MongatorBundle\MongatorBundle(),
            // ...
        );
    }

Configuration
-------------

Add Mongator to your configuration:

.. code-block:: yaml

    # app/config/config.yml
    mandango:
        default_connection: local
        connections:
            local:
                server:   mongodb://localhost:27017
                database: symfony2_local_%kernel.environment%

Activate the profiler in the developing environment:

.. code-block:: yaml

    # app/config/config_dev.yml
    mandango:
        logging: true

.. _Symfony2: http://www.symfony.com
