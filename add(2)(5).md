# 实现add(2,5)//7和add(2)(5)//7  	
	var add = function(x,r) {  
	    if(arguments.length == 1) {  
            return function(y) {return x + y;};  
		}else {  
                   return x + r;      
            }  
      }
