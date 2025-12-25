# [wm-i3] Known issues & New features

Title in bar:

- <https://wiki.archlinux.org/title/i3>
- <https://cr.i3wm.org/patch/384/>
- <https://i3-discuss.i3.zekjur.narkive.com/sQn0PEKJ/i3-ipc-window-focus-change-event>
- <https://www.mail-archive.com/i3-discuss@i3.zekjur.net/msg00867.html>
- <https://github.com/ashinkarov/i3-extras>

---

sticky indicator

---

Control redshift with keyboard shortcuts

NOTE: redshift range from 1000K to 25000K

---

toggle bar when in fullscreen mode

---

todesk每次连接都会在system tray那里产生一个新的图标。但我只想让它出现一次。

考虑可能和rule有关。可能需要把todesk设置成float。不确定是不是因为这个。

---

flameshot无法通过ESC关闭图片。这应该不是bug，只是和feh的区别。

另外，flameshot默认是置顶的

feh 放大缩小，图片始终没变，只是窗口大小在变。我希望能自动跟着缩放。

---

hyperland wayland sway之间的关系？

考虑要不要换成sway，或者hyperland或者是其他基于wayland的wm？

---

bulkmove里面，添加一个交换两个显示器中所有工作区的功能

或者说如何解决全屏模式下，能看到当前所有工作区的分布的需求。或者是如果其中一个显示器关闭了，如何能从另一个显示器获取到这个显示器的容器分布情况？

一个思路是写一个按键绑定，按下之后弹出一个terminal并且打印所有显示器上的所有工作区的所有容器名称。

---

把pm-suspend放到快捷键上

pm-suspend之后唤醒不起来

---

在全屏之后，没法看到status bar。需要寻找“不完全全屏”的方法。

---

open pdf from lf, then, win+shift+g, move container to 12, sometimes cannot work. should consider the tree node relationship.

---

对于clash for windows等应用，窗口边框不显示。

---

ctrl+shift+backslash的时候，如果一个float terminal原先不是居中，但是一旦将其加入spterm，就直接居中了。而期待的行为是如果本来已经float这种，位置不应该发生改变。

---

ydotool？

---

i3expo-ng，如果没跳转到新的，再back and forth就会有问题。比如，直接取消的情形。

原因是当跳出while循环的时候，下面的对于jump的判断，如果jump是False，就直接回到之前的workspace A。但是此时，A的上一个workspace已经变成了i3-temp。因此关键在于，需要找到“上一个的上一个”。这个如何确定？

尝试进行修复，但是发现如果一开始不切换，直接打开i3expod不跳转直接关闭，然后back and forth的时候会进入temp workspace。一旦触发bug，就会一直这样，除非手动切换一次。

---

所有ipc脚本改成异步。async或者多线程、多进程。考虑websocket等等
