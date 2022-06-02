# RSA算法实现及其原理研究 .by 吴名启
本文算法借用英国学者的等效算法而非原算法，以求更简单更直观的解释其原理
加密的数学原理本质上是数学问题的难解性例如大数的质因数分解那我们要利用什么？

这里利用了欧拉函数:
任意给定正整数n，请问在小于等于n的正整数之中，有多少个与n构成互质关系？（比如，在1到8之中，有多少个数与8构成互质关系？）
计算这个值的方法就叫做欧拉函数，以φ(n)表示。在1到8之中，与8形成互质关系的是1、3、5、7，所以 φ(n) = 4。
φ(n)的计算方法并不复杂，但是为了得到最后那个公式，需要一步步讨论。

产生一个公钥和一个私钥：

随意选择两个大的素数{\displaystyle p}p和{\displaystyle q}q，{\displaystyle p}p不等于{\displaystyle q}q，计算{\displaystyle N=pq}N=pq。
根据欧拉函数，求得{\displaystyle r=\varphi (N)=\varphi (p)\times \varphi (q)=(p-1)(q-1)}{\displaystyle r=\varphi (N)=\varphi (p)\times \varphi (q)=(p-1)(q-1)}
选择一个小于{\displaystyle r}r的整数{\displaystyle e}e，使{\displaystyle e}e与{\displaystyle r}r互质。并求得{\displaystyle e}e关于{\displaystyle r}r的模逆元，命名为{\displaystyle d}d（求{\displaystyle d}d令{\displaystyle ed\equiv 1{\pmod {r}}}{\displaystyle ed\equiv 1{\pmod {r}}}）。（模逆元存在，当且仅当{\displaystyle e}e与{\displaystyle r}r互质）
将{\displaystyle p}p和{\displaystyle q}q的记录销毁。
