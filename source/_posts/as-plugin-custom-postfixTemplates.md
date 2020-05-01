---
title: AS插件-custom postfixTemplates
categories: 
- plugin
tags: 
- plugin
toc: true
---



custom postfixTemplates 模板代码自动补全
<!-- more --> 

```
# custom templates
.d : Log.d
	ANY -> android.util.Log.d("TAG", "$methodName*:methodName()$($className*:className()$)");

.dd : Log.d + a
	ANY -> android.util.Log.d("TAG", "$methodName*:methodName()$($className*:className()$)" + " $expr$ = " + $expr$);


.s : " expr = " + expr
	ANY -> " $expr$ = " + $expr$
```


