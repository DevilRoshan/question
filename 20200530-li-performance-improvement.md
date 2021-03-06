# li-performance-improvement

> 参考链接：
>
> https://github.com/azl397985856/fe-interview/blob/master/docs/daily/2019-07-26.md
>

### 题目

页面注入50万个li怎么做提升性能？



### 解题

#### 思路

* 50万个li是基本不可能同时在页面上展现的。
* 通过分页来操作，可以动态添加元素，在滚动完成后不断向内部插入li
* 利用loading防止用户很快操作，而且视窗外的li如果过去很多就删除吧，不然也会出现性能问题

#### 代码



### 思考

* 页面元素过多其实有些事不需要渲染的，通过动态添加元素可以减少页面的dom数量，是页面更为流畅



### 扩展

* 性能上的问题，最主要的目的是如何在用户不发觉的基础上让用户可以流畅的浏览页面，尽量保证页面浏览的流畅性。
* 效果降级，如果页面很多动效，如果要保证在性能差的电脑上运行的话，应该适当的削弱动效
* 动态加载，dom只在需要的时候出现，比如antd的弹窗等弹出层，都是在最外层动态添加的，平时不生成dom。
* 分页，loading效果，这个严格意义上来说并不是是页面更优化的方案，但却是使项目更优化的方案。
* 可以通过google的performance-monitor来进行性能监控
* 有关性能问题，以后有时间在做一个优化性能的方案