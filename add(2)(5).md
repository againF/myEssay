# 实现add(2,5)//7和add(2)(5)//7  	
	var add = function(x,r) {  
	    if(arguments.length == 1) {  
            return function(y) {return x + y;};  
		}else {  
                   return x + r;      
            }  
      }  
## 进阶玩法  
	function add(x) {  
		var sum = x;  
		var tmp = function(y) {  
			sum = sum +y;  
			return tmp;  
		};  
		tmp.toString = function() { 
			return sum;  
		};  
		return tmp;  
	}  
	console.log(add(1)(2)(3));//6  
	console.log(add(1)(2)(3)(4));//10
