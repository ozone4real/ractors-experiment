# ractors-experiment
Using [Ractors](https://ruby-doc.org/core-3.0.0/Ractor.html) instead of [Threads](https://ruby-doc.org/core-3.0.0/Thread.html) for a server's worker pool.

`ractored_server` starts the server with a pool of Ractors. `threaded_server` is the threaded version. The servers basically queues up CPU-intensive tasks every 0.1..1 seconds and the workers in the pool processes them. The pool autoscales between 5 and 8 workers depending on load.
The `read_stats` script streams stats about the current state of the pool the from the server. 
Server can be started with:

```bash
./ractored_server
```

The `read_stats` client script can be used to stream stats about the server's pool with:

```bash
./read_stats stream
```

Requires Ruby version > 3.0
