---
layout: post
title:  "Correctly print int64 in x86 and x64 in C++"
---

# Note

I met some crashes when my program runs in x86 platform. And finally I found that the reason is I print an ```uint64_t``` by using ```%ld```.

## x86 and x64
```int64``` is defined as ```long int``` in 64-bit OS and ```long long int``` in 32-bit OS. When printing ```int64```, we should use ```PRId64``` instead of ```%ld``` or ```%lld```.

## C++
{% highlight cpp %}
#define __STDC_FORMAT_MACROS // don't need this in C++
#include <inttypes.h>

uint64_t a = 1;
printf("%" PRIu64, a);
{% endhighlight %}
