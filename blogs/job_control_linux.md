# Job Control in Linux

(The explanation might prone to error or low rigorousness. Take with caution!)

A job is a (group of) process(es) connected to the current shell. `jobs` lists
current jobs that you can control, e.g.,

```
[1] Stopped ./hello.sh
```

JOB_SPEC is a way to refer to the jobs. %1 means the first one in the `jobs` list.
%% means the current one (the newest one entering the list). Default is the
current one.

`bg [JOB_SPEC]` takes a foreground job to the background.
`fg [JOB_SPEC]` takes a background job up to foreground.

Usually, for a running foreground job, press `CTRL-Z` to send a SIGTSTP signal
(status symbol: letter "T") so you can interact with the shell temporarily again.
Then if you use `bg` you can have the job continue running in the background
(which equals to sending a SIGCONT signal to the pgid, i.e., `pkill -SIGCONT -g <pgid>`).
Or, you can use `fg` to bring the job back to foreground.
This trick is useful when you forget to use nohup or put a `&` sign for a command.
Further, if you want to let the process ignore SIGHUP (keep running even if you logout),
you can use
```bash
disown -h <JOB_SPEC | pid>
```
to remove the job from the `jobs` list and mark it so that it ignores SIGHUP. The pay is
you cannot bring it back to the `jobs` list again. (It cannot be referred by JOB_SPEC anymore.)

P.S.:
People use `ps aux` to see pids but I prefer `ps jax` to see not only pids but also pgid
(group id, useful for processes with child processes), so you can use
```bash
pkill -<SIG> -g <pgid>
```
to send signals to a process group instead of just one process, which is normally achieved by
```bash
kill -<SIG> pid
```

2026.11.25 3:34 a.m.

