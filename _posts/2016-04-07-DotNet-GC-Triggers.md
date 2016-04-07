---
layout: post
title: .NET GC triggers
---

.NET CLR is using these following triggers to determine whether it's necessary to perform a clean up:

- Generation 0 fills.
- The LOH reaches a treshold.
- GC.Collect is called explicitly by the app.
- The O/S reports that it is low on memory.
- AppDomain is un-loaded.
- The process is shutting down (the primary reason for this collection is to run finalizers).
