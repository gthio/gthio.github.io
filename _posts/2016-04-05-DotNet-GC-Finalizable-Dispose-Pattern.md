---
layout: post
title: Dispose Pattern
---

Any type that defineds a Finzalize method should implement dispose pattern, to deterministically disposed native resources.

Base class that overrides Object.Finalize:
{% highlight C# linenos %}

using System;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
      }

      // Free any unmanaged objects here.
      
      disposed = true;
   }

   ~BaseClass()
   {
      Dispose(false);
   }
}

{% endhighlight %}

Derived class that overrides Object.Finalize:
{% highlight C# linenos %}

using System;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
      }

      // Free any unmanaged objects here.

      disposed = true;

      // Call the base class implementation.
      base.Dispose(disposing);
   }

   ~DerivedClass()
   {
      Dispose(false);
   }
}

{% endhighlight %}
