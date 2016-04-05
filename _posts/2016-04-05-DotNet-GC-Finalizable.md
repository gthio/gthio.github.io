---
layout: post
title: .NET GC & Finalizable object
---

When an object with finalizer is dead, its finalizer is put in queue for cleanup, but the instance itself is promoted to the next generation.

References:

- [MSDN - Fundamentals of garbage collection](https://msdn.microsoft.com/en-us/library/ee787088.aspx)

