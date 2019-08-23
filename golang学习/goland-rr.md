# goland build with rr

## rr error
```bash
rr needs /proc/sys/kernel/perf_event_paranoid <= 1, but it is 3
```

resolve:

```bash
sudo sh -c 'echo 1 >/proc/sys/kernel/perf_event_paranoid'
```