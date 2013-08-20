Introduction
============

These are the official behaviors of Mongator.

.. hint::
  * **Timestampable**: saves the creation and/or update date in the documents
  * **Ipable**: saves the IP from where documents are created and/or saved
  * **Sluggable**: saves the *slug* of a field in the documents

Installation
------------

You can install them directly, from git, svn.

Directly
^^^^^^^^

You can download directly from tar_ or zip_.

Git
^^^

http://github.com/mongator/mongator-behaviors

Subversion
^^^^^^^^^^

There is an access through Subversion to the Git repository.

http://svn.github.com/mongator/mongator-behaviors

Configuration
-------------

To use these behaviors you just have to add their namespace to the class loader::

    use Symfony\Component\ClassLoader\UniversalClassLoader;

    $loader = new UniversalClassLoader();
    $loader->registerNamespaces(array(
        'Mongator\Behavior' => '/path/to/mongator-behaviors/src',
        'Mongator'          => '/path/to/mongator/src',
    ));
    $loader->register();

.. _tar: http://github.com/mongator/mongator-behaviors/tarball/master
.. _zip: http://github.com/mongator/mongator-behaviors/zipball/master
