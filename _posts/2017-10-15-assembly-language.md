---

title: Assembly language

summary: some asm starters

---

Step in, step in, step in... The source code is not available, you're in disassembly mode now.

Junior or senior engineers, aspiring and experienced - know and dread. This is an Assembly language. Nuts and bolts of computing.

<!--more-->

Psss. If you just sick of reading my reflections you can jump into the [practical staff](#dos)

A bit of a history
==================

Back in the '90s, it was crucial to know how the CPU works and the ways of building an efficient algorithm.
I remember my father sitting and analyzing C compiler output.
It wasn't possible to be a software engineer and not knowing Assembly language.
Oh, those sweet days of IDA and SoftIce!

Now
===
Since then, software development industry evolved into something much more.
Now in 2017 we have C++, Rust and Go, Java and .Net, JavaScript with endless web frameworks.
With all those technologies individuals and corporations can create quick, nice looking media reach applications and platforms.

But
===
There is always a 'but' in this imperfect world.

In any way, you'll face it:
* while clicking through a call stack;
* in critical failure report;
* in a third-party library.

If you're someone like me - lazy and reactive about it.
You know that it's simple. And you will it learn soon - when you have time.
And you never have a time.

Unless
======
You get assigned to task or project that is directly involving low-level debugging, some reverse engineering and bit wrangling.


The same thing happened to me.

My motivation
=============
Recently I got a new job and as a result technologies changed as well.
From being an ASP.NET+AngularJS developer to C/C++ and surprisingly Assembly language.


Pretty dramatic change!


No, there is no coding involved. But the binaries are always optimized and I often need to debug optimized code.
Also, there are some old libraries that don't have source code anymore. But still, have bugs.


Here I gathered some starters that I began with.

DOs
======
#### Start with something very basic. 
I am a part of a generation that prefers videos over the books.
Here is a very nice video tutorial on the x64 Assembly Language.


[![Practical x64 Assembly and C++ Tutorials](http://img.youtube.com/vi/fHE0txCjGgI/0.jpg)](https://www.youtube.com/watch?v=fHE0txCjGgI&list=PL0C5C980A28FEE68D "Practical x64 Assembly and C++ Tutorials")


#### Take a look into a [Defrag Tools](https://channel9.msdn.com/Shows/Defrag-Tools?page=16) show on Chanel 9.
It's not related to assembly language but has a lot of information about the machinery under the hood.

[![Defrag Tools](https://f.ch9.ms/thumbnail/02e22a0c-b22e-4f3f-bb40-2ca1098e92b5.png)](https://channel9.msdn.com/Shows/Defrag-Tools?page=15 "Defrag Tools")

I found these videos very interesting:
* [Defrag Tools: #13 - WinDbg](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-13-WinDbg)
* [Defrag Tools: #20 - WinDbg - Basic Commands](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-20-WinDbg-Basic-Commands)
* [Defrag Tools: #10 - ProcDump - Triggers](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-10-ProcDump-Triggers)

DON'Ts
===
#### Don't start with the book that mainly contains a description of the instructions.
It's the poorest idea I ever tried. It will kill your motivation and you will lose the focus on the important things.

#### Do not start with Intel® 64 and IA-32 Architectures Software Developer Manuals.
It's just way too much info. Most of which is not comprehensible unless you know some basics.
Also, it includes a lot of information for OS developers which is again just to much for a beginner.

#### Don't be afraid of making your hands dirty.
Apply your skills. Try to solve couple HackerRank challenges.
Here is the trick -  Assembly language is not supported.
But you can select C and embed you assembly code like this:

{% highlight c %}
static int asm_test(int a, int b)
{

    int c = 0;
    __asm__ __volatile__(".intel_syntax\n"
            "mov eax, %1\n"
            "mov edx, %2\n"
            "add eax, edx\n"
            "mov %0, eax\n"
            );
    return c;
}
{% endhighlight %}

