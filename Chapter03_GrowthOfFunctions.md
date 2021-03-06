第三章习题答案
=
#####3.1-1 f(n) g(n)是渐进非负函数，证明max(f(n),g(n)) = θ(f(n) + g(n))  
1. 假设f(n) > g(n)，根据θ定义，即证明存在正常量n0, c1, c2, 使得所有n > n0时，有 c1(f(n)+g(n)) <= f(n) <= c2(f(n)+g(n))  
2. 左边，有 c1 <= f(n)/f(n)+g(n)，因为g(n)<f(n)且非负，故f(n)/f(n)+g(n)最小趋近于1/2 (g(n) -> f(n) 时)，故c1 < 1/2  
3. 右边，有 c2 >= f(n)/f(n)+g(n)，因为g(n)非负，故f(n)/f(n)+g(n)最大趋近于1 (g(n) -> 0 时)，故c2 > 1  
即，存在某个变量c1,c2, 只要取0< c1< 1/2 , c2 >1的任意值，如 c1=1/3, c2=2,即可使证明满足。  
f(n) < g(n)时类似，略。  
证毕。  

#####3.1-2 证明对于任意常量a,b，b>0，有 (n+a)^b = θ(n^b)  
------------以下是参考了答案----------------   
按照θ定义，即证明存在正常量n0, c1, c2, 使得所有n > n0， 有 c1*n^b <= (n+a)^b <= c2*n^b  
因为 n+a <= n+|a|，当 n > |a|时有 n + a <= n + |a| < n + n = 2n   
因为 n+a >= n-|a|，当 |a| < n/2时，有 n+a >= n-|a| > n/2  
综上，当 n > 2*|a|时，有   n/2 < n+a <  2n  
因为b > 0, 故有 当 n > 2*|a|时，(n/2)^b < (n+a)^b <  (2n)^b 成立。  
故存在c1=1/2^b, c2=2^b, n0=2*|a|时，使不等式成立。证毕。  
（*注意---证明这种问题，必须**`明确指明确定的正常量c1,c2,n0.`***）  

------------以下是我的原始答案，不好。---------------  
按照θ定义，即证明存在正常量n0, c1, c2, 使得所有n > n0， 有 c1*n^b <= (n+a)^b <= c2*n^b  
1. a=0时，即证明 c1*n^b <= n^b <= c2*n^b，取c1=c2=1即可成立。  
2. 当a>0时：  
   左边 => c1 <= (1 + a/n)^b。当n>a，不等式右边最小无限趋近于1^b=1（当 n -> ∞）， 故可取c1=1使不等式成立   
   右边 => c2 >= (1 + a/n)^b。当n>a，不等式右边最大无限趋近于2^b（当n = a时），故可取c2 = 2^b使不等式成立   
3. 当a<0时：   
   左边 => c1 <= (1 + a/n)^b。当n> -a，不等式右边最小无限趋近于0（当 n = -a ）时， 故可取c1=(1+a/(-a+1)))^b使不等式成立   
   右边 => c2 >= (1 + a/n)^b。当n> -a，不等式右边最大无限趋近于1^b = 1（当n -> ∞时），故可取c2 = 1使不等式成立   
综上，证毕。   
 
#####3.1-3 解释为什么“算法A的运行时间至少是O(n^2)”这句话是无意义的。   
不明白   

#####3.1-4  2^(n+1)=O(2^n)成立吗？2^(2n)=O(2^n)成立吗？   
第一个成立；第二个不成立。  
1. 即证明存在正常量c和n0,对所有n>n0，0 < 2^(n+1) <= c*2^n  
	因为n>0，左边成立。  
	右边，2^(n+1) = 2*2^n,故对于所有的n取c=2都成立，即n0=0, c=2。  
2. 即证明存在正常量c和n0,对所有n>n0，0 < 2^(2n) <= c*2^n  
	右边， 2^(2n)=2^n*2^n，即c>2^n，不可能找出一个正常量c和n0,n>n0时 c>2^n，故不成立。  

#####3.1-5 证明定理3.1  
根据渐进符号的定义， 
f(n)=O(g(n))，故存在正常量n1,c1, 使得所有n>n1， 0<f(n)<=c1*g(n)成立；  
f(n)=Ω(g(n))，故存在正常量n2,c2, 使得所有n>n2， f(n)>=c2*g(n)>0成立；  
故存在正常量n0=max(n1,n2),c1,c2，使得不等式c2*g(n) <= f(n)<=c1*g(n)成立，符合θ符号的定义，证毕。  

#####3.1-6 证明：一个算法的运行时间是Θ(g(n))当且仅当其最坏情况运行时间O(g(n))，且最佳情况运行时间是Ω(g(n))  
没做  

#####3.1-7 证明o(g(n))∩ω(g(n))是空集   
运用反证法。假设不是空集，那么存在函数f(n)，有f(n)=o(g(n))且f(n)=ω(g(n))   
按照渐进符号o的定义，对***任意***正常量c1，存在n>n1,使得0 <=f(n) < c1*g(n)  
按照渐进符号ω的定义，对***任意***正常量c2，存在n>n2,使得0 <= c2*g(n)< f(n)  
综合以上2条， 存在n0=max（n1,n2），当n>n0时，对***任意***正常量c1和c2，有   
	c2*g(n)< f(n) < c1*g(n) => c2*g(n) < c1*g(n) => c2< c1,不符合任意c1 c2的前提条件。故f(n)不存在。证毕。 

#####3.1-8  
没做   

###-------- 思考题 ----------
#####思考题3.x  
