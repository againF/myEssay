  var a = {n: 1};  
     var b = a;  
	a.x = a = {n: 2};  
	console.log(a.x);//undefined  
	console.log(b); //{n:2}  
  作者：张开  
链接：https://www.zhihu.com/question/41220520/answer/155487071  
来源：知乎  
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。  

原代码：var a = {n: 1};  
var b = a;  
a.x = a = {n: 2};  
console.log(a.x);//undefined  
console.log(b);  
这个过程中到时发了什么？是道德的沦丧，还是......让我们来肢解下：--------1.0------------//原代码中  
var a = {n: 1};  
首先a指向内存中：{n: 1};---------2.0----------//原代码中  
var b = a;  
b指向内存中：{n: 1};----------3.0----------//原代码中  
a.x = a = {n:2}  
首先对a.x进行（左）查找，不存在，那就先赋个undefined。// 此时内存的{n:1}变化为：  
{n:1,x=undefined}  
然后现在进行右查找，右查找是个赋值表达式 a = {n: 2} ，所以得先处理这个赋值表达式。此时的战况可以类比为：// 这种写法 不要介意 叫做：gangascript  
 内存中的 {n:1,x=undefined}中的x = 还需要等待进一步的处理的赋值表达式a = {n: 2}  
重要的是，此时的a.x 已经指向了内存中的 {n:1,x=undefined}中的x，目前他正等待被赋值，所以下面在处理赋值表达式 a = {n: 2}时候，即使a发生了指向的变化，但也不再影响此刻的a.x了，因为已经对a.x进行了指向的确定，只不过他现在正在等待被赋值。----------3.1------------//原代码中  
a = {n: 2}  
指针a，被重新赋值，此时a的指向变化了，此时内存中如下：//a:指向   
{n: 2}  
//b指向   
{n:1,x=undefined}  
因为赋值操作符的返回值，是返回右边的部分：//也就是是说赋值表达式 a = {n:2}的返回值如下  
{n: 2}  
---------3.2-----------所以上面3.1中留下的尴尬局面，变成了如下：{n:1,x=undefined}的属性x = 内存中的{n: 2}  
翻译成人话就是：- 内存中对象 {n:1,x:指针}的属性x是一个指正，指向内存中的{n: 2}- 变量a，指向内存中的{n: 2}- 变量b，指向内存中的{n:1,x=指针}--------------------------4. 回到面试题目：console.log(a.x);//undefined   
console.log(b); // Object {n:1,x:Object}  
------------------------------5. 验证一下啦，科科在控制台中输入：console.log(a===b.x)  
结果true  
