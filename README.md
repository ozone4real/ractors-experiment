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

You'll see stats like the following printed:
```
pool capacity: 3
idle: 2
workers: 8
processed: 20 in 31.73919400000068 seconds
```

Running the experiment on my Macbook M3 (12 cores) shows that on average, the ractor-based worker pool processes 2x more work than the thread-based one in the same amount of time.

Requires Ruby version > 3.0
