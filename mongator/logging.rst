Logging
=======

With Mongator you can log the queries that are sent to Mongo to improve the development.

To do it you just have to pass a *PHP callable* to the mongator when you create it::

    use Mongator\Mongator;

    $logger = function(array $log) {
        print_r($log);
    }
    $mongator = new Mongator($metadata, $queryCache, $logger);

..  note::
  This functionality doesn't have **any penalty in performance** in production,
  since when it's used it's done with Mongo collection objects
  special for logging, but when it's not used (in production) it's used the
  native ones instead.
