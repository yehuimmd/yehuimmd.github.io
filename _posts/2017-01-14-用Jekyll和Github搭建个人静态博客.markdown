---
layout: post
title:  "用Jekyll和Github搭建个人静态博客"
date:   2016-06-26 13:03:42 +0800
categories: original
excerpt_separator: ~~~
---
##Ajax
- Ajax是什么？
  Ajax就是当浏览器（客户端）向服务器发送请求时用的一种技术，它的核心是XMLHttpRequest对象，他最大的特点就是向服务器请求额外的数据而无须加载页面（刷新），既*异步加载*。
- Ajax技术是怎样实现请求的？
  目前Ajax技术有两种方式实现请求：一、通过他的核心对象XHR（XMLHttpRequest的缩写）；二、通过window.fetch()方法进行请求。
     1.1通过XHR对象进行请求（原生js）代码如下：
       //1、创建XHR对象
        var request = new XMLHttpRequest();//在大多数浏览器中，在ie5、ie6中不支持这个方式

        //在ie5、ie6中兼容只需定义下面这个函数
        var request;
        if(window.XMLHttpRequest){
            request = new XMLHttpRequest();
        }else{
            request = new ActiveXObject("Microsoft.XMLHTTP");
        }

        //2、进行请求完整代码
        var xhr = new XMLHttpRequest();
        xhr.onreadystatechange = function(){
            if(xhr.readyState == 4){
                if(xhr.status >= 200 && xhr.status < 300 || xhr.status == 304){
                    //请求成功的处理函数23，服务器返回的数据存入responseText属性中
                }else{
                    //请求失败的处理函数
                }
            }
        }
        obj.open('GET/POST','url',true/false);//get和post请求，true为异步请求、false我为同步请求
        obj.send(null);//post的send(String)必须要
        
    1.2使用jQuery的$.ajax()方法实现请求，代码如下：
       $.ajax({
            type: 'GET',//请求方式
            url: 'url',//请求资源地址或请求接口
            data: {
                //请求参数
            },
            success: function(data){//服务器响应的数据都存入data中
                //请求成功处理函数
                if(data.status === '0'){
                    alert(data.message);
                } else {
                    //向自己的html添加服务器响应的数据
                }
            }
            error: function(){
                //请求失败处理函数
            }
       });
       
     2、目前市场上已经在使用window.fetch()方法，XMLHttpRequest 是一个设计粗糙的 API，不符合关注分离（Separation of Concerns）的原则，配置和调用方式非常混乱，而且基于事件的异步模型写起来也没有现代的 Promise，generator/yield，async/await 友好。Fetch 的出现就是为了解决XHR的问题
他的请求代码如下：
      window.fetch(url).then(function(response){//响应值放入response中
            return response.json();//用json()方法把相应的数据转化为javascript对象
      }).then(function(data)
            //请求成功处理函数
      }).catch(function(e){
            //请求失败处理函数
      })
      
- Ajax扩展
  Ajax为了扩充他的功能，发展了XHR2,这里我就不再详细说明，想要对Ajax的请求做详细了解的可以查看我最初的Ajax学习笔记http://www.cnblogs.com/yehui-mmd/p/5864288.html
     
