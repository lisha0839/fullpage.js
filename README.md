# fullpage.js

标签（空格分隔）： jQ 

---
fullpage.js是一个基于jQuery的插件，它能很方便、轻松地制作出全屏网站，主要功能有：
>* 支持鼠标滚动
>* 多个回调函数
>* 支持手机、平板触摸事件
>* 支持原生CSS3动画
* 支持窗口缩放
* 窗口缩放时自动调整

**github地址**：https://github.com/alvarotrigo/fullPage.js

##1、安装
通过npm安装： npm install fullpage.js

引入文件：
```
<link rel="stylesheet" type="text/css" href="jquery.fullPage.css" />

<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

<!-- 可选。当改变css3选项配置时需要引入-->
<script src="vendors/jquery.easings.min.js"></script>


<!-- This following line is only necessary in the case of using the plugin option `scrollOverflow:true` -->
<script type="text/javascript" src="vendors/scrolloverflow.min.js"></script>

<script type="text/javascript" src="jquery.fullPage.js"></script>
```

##2、HTML结构
需要注意的是包装器不能是body。当页面滑动到某一页，会自动给当前页添加class="active"。
```
<div id="fullpage">
        //页，竖向
        <div class="section">
            //幻灯片，横向
            <div class="slide"> Slide 1 </div>
            <div class="slide"> Slide 2 </div>
            <div class="slide"> Slide 3 </div>
            <div class="slide"> Slide 4 </div>
        </div>
        <div class="section">Some section2</div>
        <div class="section ">Some section3</div>
        <div class="section">Some section4</div>
    </div>
```

##3、初始化
```
$(document).ready(function() {
    $('#fullpage').fullpage({
        //配置参数
        anchors:'',
    
    });
});
```

##4、常见参数

>* **sectionsColor**：为每个section设置背景颜色
* **controlArrows**：定义是否通过箭头控制slide幻灯片，默认为true.当设置为false时，在移动设备上可通过滑动来切换
* **verticalCentered**：每一页内容是否垂直居中，默认为true
* **resize**：字体是否随窗口缩放而缩放，默认false
* **scrollingSpeed**：滚动速度，单位为毫秒，默认为700
* **anchors**：定义锚链接，默认[]，值不要与页面中任意的id或name相同，在ie下，定义时不需加#
* **lockAnchors**：是否锁定锚链接，默认为false.若为true，anchors属性定义没有效果
* **easing**：定义页面section滚动的动画方式，默认easeInOutCubic，如果要修改此项，需要引入jq.easings插件或jq ui
* **css3**：是否使用css3 transform实现滚动效果，默认true
* **loopTop**：滚动到最顶部是否连续滚动到最底部，默认false
* **loopBottom**：滚动到最底部是否连续滚动到最顶部，默认false
* **loopHorizontal**：横向slider是否循环滚动，默认true
* **autoScrolling**：是否使用插件的滚动方式，默认true。若false，则会出现浏览器自带的滚动条，将不会按页滚动，而按照滚动条默认行为滚动
* **scrollBar**：是否包含滚动条，默认false.若true,则浏览器自带滚动条出现，页面还是按页滚动，但滚动条默认行为也有效
* **paddingTop/PaddingBottom**:设置每个section顶部和底部的padding，默认0.如设置顶部或底部导航
* **fixedElements**：固定元素，默认null，需设置一个jq选择器。在页面滚动时，该元素固定不动
* **keyboardScrolling**：是否可使用键盘方向导航，默认为true
* **touchSensitivity**：在移动设备中滑动页面的敏感型，默认为5，按百分比衡量，最高100，越大则越难滑动
* **continuousVertical**：是否循环滚动，默认false。若true，页面不会像loopTop那样出现跳动，这两个不要同时设置
* **animateAnchor**：锚链接是否可控制滚动动画，默认true。若false，则锚链接定位到某个页面显示不再有动画效果
* **recordHistory**：是否记录历史，默认true，可通过浏览器的前进后退来导航。若autoScrolling：false，那么该配置也将关闭，设为false
* **menu**：绑定菜单，设定相关的属性与anchors的值对应后，就可控制滚动，默认为false
* **navigation**：是否显示导航，默认false。若为true，会显示小圆点，作为导航
* **navigationPosition**：导航小圆点位置，可设置left或right
* **navigationTooltips**：导航小圆点的tooltips设置,默认[]，注意顺序
* **showActiveTooltip**：是否显示当前页面导航的tooltip信息，默认false
* **slidesNavigation**：是否显示横向幻灯片导航，默认false
* **slidesNavPosition**：横向幻灯片导航位置，默认bottom，可设置top
* **scrollOverflow**：内容超过满屏后是否显示滚动条，默认false。若为true，则会显示滚动条，如果要滚动查看内容，需jq.slimscroll插件
* **sectionSelector**：section的选择器，默认.section
* **slideSelector**：slide的选择器，默认.slide

###方法，使用$.fn.fullpage.XXX()调用
>* moveSectionUp()向上滚动一页
* moveSectionDown()向下滚动一页
* moveTo(section,slide)滚动到第几页，第几个幻灯片，页面从1开始，幻灯片从0开始
* silentMoveTo(section，slide)和moveTo一样，但没有动画效果
* moveSlideRight()幻灯片向右滚动
* moveSlideLeft()
* setAutoScrolling(boolean)动态设置autoScrolling
* setLockAnchors(boolean)动态设置LockAnchors
* setRecordHistory(boolean)动态设置
* setScrollingSpeed(ms)动态设置scrollingSpeed
* setAllowScrolling(boolean,[directions])添加或删除鼠标滚轮/滑动控制，第一个参数为true为启用，后面方向可为all\up\down\left\right,可使用多个，逗号分隔
* destroy(type)销毁fullpage特校，type可不写；或用all不写type,样式、特效均销毁
* reBuild()重新更新页面和尺寸，通过ajax请求后改变了页面结构后，重建效果

###回调函数
>* afterLoad：function(anchorLink,index){console.log(anchorLink,index)}滚动到某一section，且结束滚动后会触发一次回调。anchorLink为锚链接名称，index为序号，从1开始计算
* onLeave:function(index,nextIndex,direction){}在离开一个section时，就会触发一次回调，index是离开页面的序号，从1开始；nextIndex是滚动到目标页面的序号，从1开始；direction判断往上还是往下滚动，up或down.通过return false可取消滚动
* afterRender:function(){}页面结构生成后的回调函数
* afterResize:function(){}浏览器窗口尺寸改变后的回调函数
* afterSlideLoad:function(anchor,index,slideAnchor,slideIndex)滚动到某一幻灯片后的回调

###<img data-src="xx.png"> 用data-src代替src可实现懒加载图片或视频



