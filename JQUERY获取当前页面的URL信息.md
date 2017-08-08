# JQUERY获取当前页面的URL信息

设置或获取对象指定的文件名或路径。  
window.location.pathname  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.pathname); 则输出：/topic/index  

设置或获取整个 URL 为字符串。  
window.location.href  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.href); 则输出：http://localhost:8086/topic/index?topicId=361  


设置或获取与 URL 关联的端口号码。  
window.location.port  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.port); 则输出：8086 


设置或获取 URL 的协议部分。  
window.location.protocol  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.protocol); 则输出：http: 


设置或获取 href 属性中在井号“#”后面的分段。  
window.location.hash 


设置或获取 location 或 URL 的 hostname 和 port 号码。  
window.location.host  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.host); 则输出：http:localhost:8086 


设置或获取 href 属性中跟在问号后面的部分。  
window.location.search  
例：http://localhost:8086/topic/index?topicId=361  
alert(window.location.search); 则输出：?topicId=361  
window.location 


属性　　　　　　　　　  
hash设置或获取 href 属性中在井号“#”后面的分段。  
host设置或获取 location 或 URL 的 hostname 和 port 号码。  
hostname设置或获取 location 或 URL 的主机名称部分。  
href设置或获取整个 URL 为字符串。  
pathname设置或获取对象指定的文件名或路径。  
port设置或获取与 URL 关联的端口号码。  
protocol设置或获取 URL 的协议部分。  
search设置或获取 href 属性中跟在问号后面的部分。  
