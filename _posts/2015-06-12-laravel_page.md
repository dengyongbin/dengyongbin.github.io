---
layout:     post
title:      laravel page自定义
category: blog
description: laravel 自定义分页组件的实现，显示首页、尾页、上一页、下一页等。
---    
          

## 分页效果图      
![Alt Text](../images/2015-06-12-01.png)      

## 代码注意

```
要自定义产生自己的链接样式，可以修改vendor的分页组件BootstrapPresenter类，
laravel默认上一页、下一页是》《样式，这个可以修改Presenter类的getPrevious方法、
getNext方法的$text      
```

## 使用laravel的links方法产生分页代码，自定义page视图
```js
	<div id="kkpager">
	  <?php $borrow_list->appends($param)->links('web.page'); ?>
	</div>
```

## page视图代码
```php
<?php
$presenter = new Illuminate\Pagination\BootstrapPresenter($paginator);
?>
<span class="infoTextAndGoPageBtnWrap">
    <span class="totalText">
        <span class="currPageNum">{{ $paginator->getCurrentPage() }}</span>
        <span class="totalInfoSplitStr">/</span>
        <span class="totalPageNum">{{ $paginator->getLastPage() }}</span>
    </span>
</span>
<span class="pageBtnWrap">
    @if($paginator->getCurrentPage() > 1)
        <a href="{{ $paginator->getUrl(1) }}">首页</a>
    @else
        <span class="disabled">首页</span>
    @endif
    <?php echo $presenter->render(); ?>
    @if($paginator->getCurrentPage() < $paginator->getLastPage())
        <a href="{{ $paginator->getUrl($paginator->getLastPage()) }}">尾页</a>
    @else
        <span class="disabled">尾页</span>
    @endif
</span>
```

## css样式代码
```css
#kkpager{
	height:100px;
	color:#999;
	font-size:16px;
	text-align:center;
}
#kkpager a, #kkpager span{ display:inline-block;}
#kkpager a{
	height:22px;
	line-height:22px;
	float:left;
	border:1px solid #ccc;
	display:inline;
	padding:3px 10px 3px 10px;
	margin-right:5px;
	border-radius:16px;
	-moz-border-radius:16px;
	-webkit-border-radius:16px;
	cursor: pointer;
	background: #fff;
	text-decoration:none;
	color:#999;
}

#kkpager span.disabled{
	height: 22px;
	line-height: 22px;
	float: left;
	display: inline;
	padding: 3px 10px 3px 10px;
	margin-right: 5px;
	border-radius:16px;
	-moz-border-radius:16px;
	-webkit-border-radius:16px;
	border:1px solid #DFDFDF;
	background-color:#FFF;
	color:#DFDFDF;
}
#kkpager span.curr{
	height:22px;
	line-height:22px;
	float:left;
	display: inline;
	padding:3px 10px 3px 10px;
	margin-right:5px;
	border-radius:16px;
	-moz-border-radius:16px;
	-webkit-border-radius:16px;
	background:#45d1af;
	color:#fff;
}
#kkpager span.normalsize{
}
#kkpager_gopage_wrap{
	position:relative;
	left:0px;
	top:0px;
}
#kkpager_btn_go {
	width:44px;
	height:18px;
	border:0px;
	overflow:hidden;
	line-height:140%;
	padding:0px;
	margin:0px;
	text-align:center;
	cursor:pointer;
	background-color:#FF6600;
	color:#FFF;
	position:absolute;
	left:0px;
	top:-2px;
	-moz-border-radius: 3px;
	-webkit-border-radius: 3px;
	display:none;
}
#kkpager_btn_go_input{
	width:36px;
	height:14px;
	color:#999;
	text-align:center;
	margin-left:1px;
	margin-right:1px;
	border:1px solid #DFDFDF;
	position:relative;
	-moz-border-radius: 3px;
	-webkit-border-radius: 3px;
	left:0px;
	top:0px;
	outline:none;
}
#kkpager_btn_go_input.focus{
	border-color:#FF6600;
}

#kkpager .pageBtnWrap{
	width:auto;
	height:50px;
    margin-top:30px;
}

#kkpager .spanDot{
	margin-right:5px;
}
#kkpager .currPageNum{
	color:#FD7F4D;
}

#kkpager .infoTextAndGoPageBtnWrap{
	display:inline-block;
	line-height:90px;
	padding-right:10px;
	vertical-align: top;
}
```


