---

title: Assembly language. Part 2 Bruteforcing Project Euler 1 Multiples of 3 and 5

summary: Remember in the previous blog post I proposed to use your skills in Assembly. Here is my try...

---

Remember in the previous blog post I proposed to use your skills in Assembly. Here is my try...

<!--more-->

Here is my super-dirty solution for Project Euler #1. Yeah it is a bruteforce way. I know that there is O(1) solution. But there is nothing interesting to do with Assembly language.

The code below is a C code that you can insert into HackerRank. Or compile with gcc.

{% highlight c %}
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

static int func(unsigned long long src)
{
    int dst; 
    __asm__ __volatile__(".intel_syntax noprefix\n"
    // rcx - a counter that decremented on every cycle of the loop
    //       Also it came as a first function parameter (since fastcall is used).
    // r8d - used to accumulate the end result
    // rax - used by div and a return value
    // r9  - a division remainder
    "mov r8, 0;"    // tmpAcc = 0
    "mov r9, 0;"    // 
    "mov r10, 0;"    // 
    "mov rax, 0;"    // result = 0 (rax is return value)

    "cmp rcx, 0;"
    "je Finished;"    // if(counter == 0) return;

    "do:;"            // while(true)
    "add r8, r10;"    // tmpAcc += 
    "mov r10, 0;"

    "dec rcx;"            // counter--
    "jz Finished;"        // if(counter == 0) break;

    "mov rdx, 0;"        // tmp = counter % 3
    "mov rax, rcx;"
    "mov r9, 3;"
    "div r9;"

    "cmp dx, 0;"        // is there any remainder?
    "cmove r10, rcx;"

    "je do;"

    "mov rdx, 0;"
    "mov rax, rcx;"
    "mov r9, 5;"
    "div r9;"

    "cmp dx, 0;"        // is there any remainder?
    "cmove r10, rcx;"

    "jmp do;"

    "Finished:;"
    "mov rax, r8;"
    ".att_syntax"
     : "=a" (dst)// get ouput from RAX
     : "c" (src)    // accept input parameter throught the RCX regixter
     : "r8", "r9", "r10", "rdx"); // clobbered register
    
    return dst;
}

int main(){
    int t; 
    
    scanf("%d",&t);    
    for(int a0 = 0; a0 < t; a0++){
        int sum = 0;
        int n;        
        scanf("%d",&n);
        printf("%d\r\n", func((unsigned long long)n));
    }
    return 0;
}
{% endhighlight %}