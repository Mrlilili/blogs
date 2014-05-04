HTML5应用缓存基础知识
===

下面简单的介绍一下应用缓存的基本知识：
#####1. 应用缓存的作用
让浏览器内WebApp像本地应用一样，多数或者全部资源都保存在本地，在没有网络，或者服务器宕掉的情况下，仍然能够使用大多数或者全部功能。有三个特点：离线浏览，更快的速度，以及减轻服务器负担。  

#####2. 使用了应用缓存的页面的加载流程
1. 当浏览器访问一个包含了应用缓存的页面时，如果应用缓存已经存在，那么直接使用应用缓存，否则浏览器加载文档，然后获取`manifest`文件列出的CACHE和FALLBACK文件，生成第一版的应用缓存。  
2. 

#####3. 使用方法：
###### 1. 创建`manifest`文件
以下是`manifest`文件的模板
```
CACHE MANIFEST
# verison 1
CACHE:
path/to/cached/file/a.html
path/to/cached/file/b.js
NETWORK:
path/to/network/request/a
path/to/network/folder/b
FALLBACK:
path/to/network/request/c path/to/fallback/file/c
path/to/network/folder/d path/to/fallback/file/d
```
`manifest`文件对路径，文件名和后缀名没有限制。但是一般推荐放在项目根目录下面，因为在`manifest`文件里面定义的相对路径是相对于`manifest`文件的，而不是引用该`manifest`文件的html页面。后缀名虽然没有限制，但是该文件的MIME类型必须是`text/cache-manifest`，因此假如后缀名是`manifest`，那么必须做如下配置：
Apache： 在相应的`.htaccess`文件中增加 `AddType text/cache-manifest .manifest`  
Nginx： 在`mime.types`文件中加上`text/cache-manifest manifest`;

第一行必须是`CACHE MANIFEST`；  
第二行建议是注释，标明当前`manifest`文件版本。注释以`#`开始。为什么要有这样一个注释呢，这是因为浏览器在判断是否需要更新应用缓存时，是根据当前获得的`manifest`文件内容和缓存中的`manifest`文件内容有没有不同，如有不同，才会更新应用缓存。有时候我们仅仅更改某个文件的内容，但是`manifest`文件却不需要更改，但是如果不更改，那么浏览器就不会去获取新的资源文件。所以一个最佳实践就是一旦有文件修改，总是去更新`manifest`文件中的版本号。  
在以后的若干行中，可以是
1）空白行  
2）注释行  
3）段落标题 可以是`CACHE:`，`NETWORK:`或`FALLBACK:`，可以出现零次或多次。  
4）段落数据  
CACHE段落以`CACHE:`段落标题（可省略）开始，每行都是一个URL，表示该资源要被缓存起来。不允许使用通配符`*`。  
NETWORK段落以`NETWORK:`段落标题开始，每行都是一个URL，代表一条资源或者该资源目录下的一组子资源，表示这些资源总是从互联网获取。  
FALLBACK段落以`FALLBACK:`段落标题开始，每行都包含两个URL，第一个URL是资源地址，代表一条资源或者该资源目录下的一组子资源，表示这些资源总是从互联网获取，第二个URL是后备资源地址，该资源会放入应用缓存中。如果前者获取失败，则从应用缓存获取后备资源替代。  

######2. 引入`manifest`文件
```html
<html manifest="example.manifest"> 
  ...
</html>
```

######3


#####参考
[MDN](https://developer.mozilla.org/zh-CN/docs/HTML/Using_the_application_cache)


