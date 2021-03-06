# CPU profiling

https://wiki.dlang.org/Development_tools#CPU_profiling

## Tracing

### Built-in `-profile`

* On Linux, x86_64's `rdtsc` instruction is used.

```console
$ dmd -profile ...
```

or

```console
$ dub build --build=profile
```

### callgrind

Command:

```console
$ valgrind --tool=callgrind --callgrind-out-file=callgrind.out.slow.1 ./slow
```

D's symbols will need to be demangled by `ddemangle`.

```console
$ callgrind_annotate callgrind.out.slow.1| ddemangle
```

## Sampling

### perf

- https://code.dawg.eu/profiling-with-perf-and-friends.html

#### perf-stat

- https://perf.wiki.kernel.org/index.php/Tutorial#Counting_with_perf_stat

```console
$ perf stat -r 5 -- command
```

#### perf-record

- https://perf.wiki.kernel.org/index.php/Tutorial#Sampling_with_perf_record
- https://perf.wiki.kernel.org/index.php/Tutorial#Sample_analysis_with_perf_report

```console
$ perf record -- command
$ perf report
```
