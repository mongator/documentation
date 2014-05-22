Events
=======

Mongator provides support for `Symfony\EventDispacther`_ library, through the method `Mongator::setEventDispatcher`
php::
	use Symfony\Component\EventDispatcher\EventDispatcher;
	
	$eventDispatcher = new EventDispatcher();
	$mongator->setEventDispatcher($eventDispatcher);

In every insert, update or delete over the documents the following event will be triggered:

.. hint::
  * **pre.insert**: before inserting
  * **post.insert**: after inserting
  * **pre.update**: before updating
  * **post.update**: after updating
  * **pre.delete**: before deleting (not for EmbeddedDocuments)
  * **post.delete**: after deleting (not for EmbeddedDocuments)


The event name pattern can be configured with the key `eventPattern` in the config class, in sprintf format: 
php::
	array(
	    'Model\Article' => array(
	        // ...
	        'eventPattern' => 'article.event.%s',
	    ),
	);

If no one is configured, the default pattern for this class, will be: `mongator.model.article.%s` where the %s is the name of the event.

.. _Symfony\EventDispacther:  http://symfony.com/doc/current/components/event_dispatcher/introduction.html
