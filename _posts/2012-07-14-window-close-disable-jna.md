---
layout:     post
title:      "JNA 应用：调用 Windows dll 实现禁用窗口关闭按钮"
date:       2012-07-14
author:     "Aaron"
tags:
    - Java
---

JNA 是 [Java Native Access](https://github.com/twall/jna) 的缩写，顾名思义，提供访问本地 Native 代码的功能。
以前是 Sun 在维护，现在是托管在 Github 的开源项目。

有个运行在 Console 的 Java 程序作为服务，为了避免不小心鼠标晃到关闭按钮，服务就挂了，还是不让点得到的好。

```java
public interface User32 extends StdCallLibrary {
	User32 INSTANCE = (User32) Native.loadLibrary("user32", User32.class);
	Pointer FindWindowA(String winClass, String title);
	Pointer GetSystemMenu(Pointer hWnd, int bRevert);
	int RemoveMenu(Pointer hMenu, int nPos, int flags);
	int DrawMenuBar(Pointer hWnd);
}
```

新建一个接口为 User32 继承自 JNA 的 StdCallLibrary，声明需要用到的方法。
调用：

```java
final User32 user32 = User32.INSTANCE;

Pointer hWnd = user32.FindWindowA(null, titleName);
Pointer sysMenu = user32.GetSystemMenu(hWnd, 0);

if (hWnd == null) {
	//没找到窗口
}
System.out.println("Found window " + hWnd + ", menu: " + sysMenu);

int SC_CLOSE = 0xF060;
if (user32.RemoveMenu(sysMenu, SC_CLOSE, 0x0) == 1) {
	//重绘菜单
	user32.DrawMenuBar(hWnd);
}
```

另外，改变 Console Title 的方法：

```java
System.out.print("\033]0;" + title + "\007");
```
