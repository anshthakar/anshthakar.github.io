---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

---
layout: post
title: "First Notes"
---

I'm Ansh, a high school student. This blog is where I'll document what I learn
about systems I/O: how programs actually move bytes between disk, memory,
the kernel, and the network, and what it costs.

## Why this

Most programmers treat I/O as a black box. You call `read()`, data shows up.
But underneath there are syscalls, context switches, the page cache, and
copies you never asked for. Those costs decide whether a program is fast
or slow far more often than clever algorithms do. I want to understand
them by through measurement.

## The plan

Three projects, each building on the last:

1. **File copy experiment.** Copy a large file using different buffer
   sizes, stdio, `mmap`, and `sendfile`, and measure where the time goes.
2. **Fast log parser.** Parse multi-gigabyte files and separate I/O cost
   from parsing cost.
3. **A server, three ways.** Blocking threads vs `epoll` vs `io_uring`,
   under load.

## Ground rules

Every post will include the code, the benchmark setup, the hardware it
ran on, and the raw numbers. If I can't explain a result, I'll say so
instead of guessing. If I get something wrong, I want to hear about it.

## Next up

How much does a syscall actually cost? I'm going to copy a 2 GB file one
byte at a time, then 64 KB at a time, and find out how bad the difference is.
