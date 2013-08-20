Sluggable
=========

The *Sluggable* behavior saves the slug of one field in another one.

Configuration
-------------

::

    array(
        'Model\Article' => array(
            'fields' => array(
                'title'   => 'string',
                'content' => 'string',
            ),
            'extensions' => array(
                array('class' => 'Mongator\Behavior\Sluggable', 'options' => array('fromField' => 'title')),
            ),
        ),
    );

.. hint::
  **Options**:

  * **fromField**: field used to generate the slug (required)
  * **slugField**: field used to store the slug (*slug* by default)
  * **unique**: if the slugs have to be unique (enabled by default) (if it is enabled a unique index is created)
  * **update**: if the slugs can be updated if the field from where the slug is created is modified (disabled by default)
  * **builder**: function that converts the base string to slug (*Mongator\Behavior\Util\Sluggable::slugify()* by default)

Usage
-----

::

    $article = $mongator->create('Model\Article')
        ->setTitle('Mongator is ultrafast!')
        ->save()
    ;

    echo $article->getSlug(); // mongator-is-ultrafast

    $article2 = $mongator->create('Model\Article')
        ->setTitle('Mongator is ultrafast!')
        ->save()
    ;

    echo $article2->getSlug(); // mongator-is-ultrafast-2
