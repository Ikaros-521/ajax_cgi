## 相关说明

操作系统：CentOS7 

Web服务器：[BOA](http://www.boa.org/) 

语言：HTML+JS+C 

演示了网页如何把数据通过AJAX发给后台CGI和后台CGI如何把数据返回到网页的指定控件显示

源码参考：[AJAX_CGI](http://www.pudn.com/Download/item/id/2260088.html)

BOA的搭建参考：[Linux下嵌入式Web服务器BOA和CGI编程开发](https://blog.csdn.net/Ikaros_521/article/details/102610768)

小案例实战参考：[嵌入式web服务器BOA+CGI+HTML+MySQL项目实战——Linux](https://blog.csdn.net/Ikaros_521/article/details/102801453)

源码下载：[GitHub](https://github.com/Ikaros-521/ajax_cgi)，[码云](https://gitee.com/ikaros-521/ajax_cgi)

## 效果展示

### **ajaxtest1.html**
![在这里插入图片描述](https://images.gitee.com/uploads/images/2019/1204/122946_de54eb11_5140590.png)
**实现效果：在对应输入框内输入内容调用对应函数，非空，就显示cgi程序返回的内容**

```c
	if(strstr(lenstr,"txtIDA")!=NULL)
	{
	    printf("ianLiu@yeah.net\n\n");
	}
	if(strstr(lenstr,"txtIDB")!=NULL)
	{
	    printf("Liuyixu\n\n");
	}
```
**然后给对应控件进行赋值**

```javascript
document.getElementById("txtIDB").innerHTML=xmlhttp.responseText;
```
![在这里插入图片描述](https://images.gitee.com/uploads/images/2019/1204/122946_9e5eb29a_5140590.png)
![在这里插入图片描述](https://images.gitee.com/uploads/images/2019/1204/122946_16f6ad0b_5140590.png)

---

### **ajaxtest3.html**
![在这里插入图片描述](https://images.gitee.com/uploads/images/2019/1204/122946_88eb0548_5140590.png)
**点击按钮**

```javascript
<input type="submit" value="get_info" onclick="get_info()" />
```

**实现获取cgi发送回来的json字符串**

```c
	if(strstr(lenstr,"get_info") != NULL)
	{
	    printf("{\"A\":\"%s\",\"B\":\"%s\"}",ip,prot);
	}
```
**转json对象，给对应控件赋值的效果**

```javascript
//将接收到的字符串存入jsonstr
var jsonstr = xmlhttp.responseText;
alert("json:"+jsonstr);
// 将jsonstr转换为json对象 json
var json = JSON.parse(jsonstr);
```

```javascript
    if(json[name1]){
        var value = json[name1];
        // 直接给id为name1的控件赋值
        document.getElementById(name1).innerHTML = value;
    }
    if(json[name2]){
        var value = json[name2];
        document.getElementById(name2).innerHTML = value;
    }
```

![在这里插入图片描述](https://images.gitee.com/uploads/images/2019/1204/122946_759a2c4f_5140590.png)
