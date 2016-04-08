---
layout: post
title: .NET GC Monitoring
---

Few ways to monitor the garbage collector:

- GC class static methods

{% highlight C# linenos %}

//To see how many collections have occurred of specific collection within in a process
Int32 CollectionCount(Int32 generation);

//To see how much memory currently being used by objects in the managed heap within a process
Int64 GetTotalMemory(Boolean forceFullCollection);

{% endhighlight %}

- PerfMon.exe, .NET framework performance counters
- CLR profiler. This tool offers call profiling, heap snapshots and memory use timelines. 
- SOS Debugging Extension (SOS.dll). This allows us to see how much memory is allocated within managed heap, displays all objects registered in finalization quque, shows the roots that keeping an object alive, etc.