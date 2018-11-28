###mac 键盘映射 karabiner
今天在vim编辑的时候觉得用mac的方向键有点麻烦 需要移动我的小右手，然后就搜个映射方案。
百度出来了 karabiner。

[官网](https://pqrs.org/osx/karabiner/index.html.en)

安装什么的就不说了， 安完了会有一个小图标![](http://images2015.cnblogs.com/blog/1034168/201612/1034168-20161202171134490-1851597917.png)
这个方框

![](http://images2015.cnblogs.com/blog/1034168/201612/1034168-20161202171853974-1918666688.png)

这是软件界面， 基本有很多设置满足各种需求，但是我好像没看见我的需求（把方向键映射为ctl＋HJKL）

然后点misc&Uninstall->open private.xml

直接写配置文件

```
<?xml version="1.0"?>
<root>
<item>
    <appendix>Change Arrow to Control +hjkl </appendix>
    <identifier>private.swap_space_and_tab3</identifier>
    <autogen>__KeyToKey__ KeyCode::H,VK_CONTROL, KeyCode::CURSOR_LEFT</autogen>
    <autogen>__KeyToKey__ KeyCode::J,VK_CONTROL, KeyCode::CURSOR_DOWN</autogen>
    <autogen>__KeyToKey__ KeyCode::K,VK_CONTROL, KeyCode::CURSOR_UP</autogen>
    <autogen>__KeyToKey__ KeyCode::L,VK_CONTROL, KeyCode::CURSOR_RIGHT</autogen>
  </item>

</root>

```

很简单，  只不过我开始映射写反了， 导致出了点问题， 可能中外思维习惯不一样。

然后我就可以愉快的撸代码了。