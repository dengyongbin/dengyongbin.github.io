---
layout:     post
title:      laravel page自定义
category: blog
description: laravel 自定义分页组件的实现，显示首页、尾页、上一页、下一页等。
---    

# 实现细节：          

## 分页效果图      
![Alt Text](../images/2015-06-12-01.png)      

## 代码片段      

```html
<div id="kkpager">
   // $param为其他查询参数，数组类型，在views目录新建page.blade.php页面
   {{ $borrow_list->appends($param)->links('web.page') }}
</div>
```

