Using
=====

You can use Mongator in a normal way.

You can access to the mongator in the container::

    $mongator = $container->get('mongator');

The mongator is initialized also automatically (in a lazy way) if you use some
functionality in the documents that require it::

    // creating
    $article = $mongator->create('Model\Article');
    $article->setTitle($title);
    $article->save();

    // quering
    $articles = $mongator->getRepository('Model\Article')->createQuery();

    // ...
