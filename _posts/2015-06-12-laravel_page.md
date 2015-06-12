---
layout:     post
title:      laravel page自定义
category: blog
description: laravel 自定义分页组件的实现，显示首页、尾页、上一页、下一页等。
---    
          

## 分页效果图      
![Alt Text](../images/2015-06-12-01.png)      

## 代码片段

```
要自定义产生自己的链接样式，可以修改vendor的分页组件BootstrapPresenter类，laravel默认上一页、下一页是》《样式，这个可以修改Presenter类的getPrevious方法、getNext方法的$text      

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

