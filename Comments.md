## 3. 注释 ##

_"当代码与注释不一致时，两者很可能都是错的"_ -- Norm Schryer

注释应该描述发生了什么，如何做的，参数的含义，使用和修改了哪些全局变量以及约束或Bugs。避免给那些本身很清晰的代码加注释，因为这些注释信息将很快的过时。注释与代码不一致将会带来负面影响。短小的注释应该是关于做什么的，比如"计算有意义的值"，而不是关于"怎么做"的，例如"值的总和除以n"。C不是汇编；在头3-10行的区域添加注释，说明代码总体是做什么的，经常要比为每行添加注释说明微逻辑更加有用。

注释应该为那些令人不悦的代码作出"辩护"。辩护应该是这样的：如果使用正常的代码，一些糟糕的事情将会发生。但仅仅让代码运行的更快还不足以让这些hack代码显得合理化；而是应该将那些在不使用hack代码时令人无法接受的性能数据展示出来。注释应该对着写不可接受的行为作出解释，并告诉大家为什么使用Hack代码可以很好的解决这个问题。

那些用于描述数据结构，算法等的注释应该以块注释的形式存在。块注释起始以`/*`占据1-2列，`*`放在每行注释前面的第二列，块注释最后以占据2-3列的`*/`结尾。另外一个候选方案是每行注释文字前面用`*`占据1-2列，块注释以占据1-2列的`*/`收尾。

```

/*
 *    Here is a block comment.
 *    The comment text should be tabbed or spaced over uniformly.
 *    The opening slash-star and closing star-slash are alone on a line.
 */

/*
** Alternate format for block comments
*/
```


注意

`grep '^.\e*'`

将匹配文件中所有的注释。特别长的块注释，诸如持久讨论或版权声明，经常以占据1-2列的`/*`开始，每行注释文字前没有`*`，并最终以占据1-2列的`*/`结束。函数内部很适合使用块注释，块注释应该与其描述的代码拥有相同的缩进。独立的单行注释也应该与其说明的代码缩进一致。

```
if (argc > 1) {
    /* Get input file from command line. */
    if (freopen(argv[1], "r", stdin) == NULL) {
        perror (argv[1]);
    }
}
```

特别短的注释可以与其描述的代码放在同一行上，并且要通过tab与代码语句分隔开来。如果针对一块代码有不止一个短注释，这些注释应该具有相同的缩进。

```
if (a == EXCEPTION) {
    b = TRUE;                /* special case */
} else {
    b = isprime(a);            /* works only for odd a */
}
```