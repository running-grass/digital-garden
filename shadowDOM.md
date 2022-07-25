是[[Web组件]]的相关技术之一

样式和宿主所在的document是隔离的，不但里面的修改不会影响到外面。而且外面的钥匙也不会作用到里面。主要是这样固然有利于样式的组件化，但是一些全局样式的方案就不能使用了。例如 [[Tailwind css]].


想要在外面改变shadowdom的内部样式有四种方式
1. 最简单的通过在内部使用 link 标签来引入外部样式文件
2. 通过[自定义属性](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)可以把一些主题色和其他数值变量传入shadowdom中，例如在外层定义 --color-bg: red; 然后在里边用 color: var(--color-bg);
3. 基于[constructible stylesheets](https://github.com/WICG/construct-stylesheets/blob/gh-pages/explainer.md)在外面用js构建样式表，然后添加到相应的影子dom
4. 基于 [part 属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::part)，类似于 x-bar::part(some-box) { ... }



# 相关链接
- [Explainer: CSS Shadow ::part and ::theme](https://github.com/fergald/docs/blob/master/explainers/css-shadow-parts-1.md) 关于使用part属性的原因和用法
