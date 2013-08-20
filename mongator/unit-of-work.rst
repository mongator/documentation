Unit Of Work
============

Mongator implements the `Unit Of Work`_ pattern, which simply means
"send all database operation at once".

Let's see an example::

    // prepare database operations
    $author = $mongator->create('Model\Author')->setName('pablodip');
    $mongator->persist($author);

    $category1 = $mongator->create('Model\Category')->setName('MongoDB');
    $category2 = $mongator->create('Model\Category')->setName('PHP');
    $mongator->persist(array($category1, $category2));

    $article = $articleRepository->createQuery(array('name' => 'Mondongo'))->one();
    $article
        ->setName('Mongator')
        ->setAuthor($author)
        ->addCategories(array($category1, $category2))
    ;
    $mongator->persist($article);

    $articles = $articleRepository->createQuery(array('type' => 'foo'))->all();
    $mongator->remove($articles);

    // send all database operations at once
    $mongator->flush();

Like you can see this is a really powerful way to work, because you can
prepare all the database operations, and when all of them are ready, you
just have to send them to the database.

MongoDB does not have transactions, so this is probably the best way you
can work if you want avoid as much as possible database inconsistency
because of application breaks.

And this is also the best way to get the maximum database performance, because
Mongator does that the database operations are as efficient as possible.

.. _Unit of Work: http://martinfowler.com/eaaCatalog/unitOfWork.html
