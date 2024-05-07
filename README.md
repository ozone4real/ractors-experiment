# ractors-experiment
Using [Ractors](https://ruby-doc.org/core-3.0.0/Ractor.html) instead of [Threads](https://ruby-doc.org/core-3.0.0/Thread.html) for a server's worker pool.

`ractored_server` starts the server with a pool of Ractors. `threaded_server` starts the server with a pool of Threads. The server basically queues up CPU-bound tasks and the workers in the pool processes them.
The `read_stats` script streams stats about the current state of the pool the from the server. 
Server can be started with:

```bash
./ractored_server
```

The `read_stats` client script can be used to stream stats about the server's pool with:

```bash
./read_stats stream
```
