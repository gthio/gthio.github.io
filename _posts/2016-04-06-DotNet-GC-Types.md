---
layout: post
title: .NET GC types
---

.NET CLR provides these following types of GC:

- Workstation GC, there is a single thread that performs collection.
    - Concurrent GC is default flavor. There is separate and dedicate highest priority thread that executes collection from start to finish.
    - Non-Concurrent GC suspends application threads during collection.
- Server GC, occurs on a set of GC threads (1 GC thread for each processor). All application threads are suspended, which allow collection to complete sooner.


{% highlight xml linenos %}

<configuration>
  <runtime>
    <gcServer enabled="true" />
    <gcConcurrent enabled="false" />
  </runtime>
</configuration>

{% endhighlight %}