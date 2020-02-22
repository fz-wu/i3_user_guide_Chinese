# i3 WM 官方用户指南

作者: Michael Stapelberg

中文译者: 法宗

michael@i3wm.org

源地址: https://i3wm.org/docs/userguide.html

这里提供我的配置文件: https://github.com/fz-wu/.config/blob/master/i3/config

如有问题,欢迎指正.

##  1. 默认键位绑定

对于阅读障碍患者,这里有一张默认键位绑定概览.

使用$mod(Alt):

![mod](https://i3wm.org/docs/keyboard-layer1.png)

使用Shift+$mod:

![Shift+mod](https://i3wm.org/docs/keyboard-layer2.png)



红键是修饰键(这里显示的是默认键位),蓝键是你的homerow.

> 注: 需要按红建之后, 按下蓝键触发相应功能.
>
> homerow不知怎么翻译

注意: 当没有配置i3的配置文件时,i3会为你创建一个.其中无论你是用什么键盘布局,键的位置都会与你在上图中看到的位置匹配.如果你倾向于使用配置文件,那么请拒绝使用i3提供的配置,并在`/etc`目录创建`i3/config`文件.

> 注: 这里有点不清楚.第一使用i3会让你选择$mod键,默认使用Alt,mac用户建议使用command键.
>
> 你可以在`/etc/` 或`~/` 或 `~/.config`创建配置文件.优先级递增.



## 2. 使用 i3

在本指南中,关键字`$mod`将用于引用已配置的修饰符.`Alt`键(Mod4)是默认的修饰键.`Win`键是更受欢迎.因为可以避免与其他的软件快捷键冲突.

> 注: 译者建议选择`Alt`键,使用`Win`键需要移动手掌,这很不方便.当然还有一种选择,你可以将两个键的绑定互换,然后使用`Win`键.

### 2.1 打开和移动终端

一个非常基础的操作是打开新的终端.默认打开终端的键位是`$mod+Enter`在默认的配置中是`Alt+Enter`.按下`$mod+Enter`后将打开一个终端.他将覆盖整个屏幕.

<img src="https://i3wm.org/docs/single_terminal.png" alt="new terminal"  />

如果你现在在打开一个终端,它将会出现在第一个终端的后面,把屏幕一分为二.根据你的显示器i3将会选择选择水平(横屏)还是垂直(竖屏)放置它们.

![](https://i3wm.org/docs/two_terminals.png)

在两个终端中移动焦点,可以直接使用方向键(像vi中那样).但是在i3中,这些键被使用了(在vi中，为与大多数键盘布局兼容，键被向左移动了一个).因此`$mod+j`是向左,`$mod+k`是向下,`$mod+l`是向上,`$mod+;`是向右.因此,要在两个终端之间进行切换,可以使用`$mod+k`或`$mod+l`.当然,你也可以使用方向键.

> 注: 为了使操作和vim一致,建议修改配置文件

这时,你的工作区(workspace)被分成了两个终端.默认是水平排列的.每一个窗口都可以重新分成水平和垂直,和整个工作区一样.这个术语(工作区)是即指实际包含X11窗口(如终端或浏览器)容器的“窗口”,或包含一个到多个窗口容器的“拆分容器”.

待完成: 树的图片

在你打开新程序之前,可以按`$mod+v`来选择垂直分割,按`$mod+h`选择水平分割.

### 2.2 改变容器布局

一个分割容器是下面三个分割布局之一:

- 平铺式默认)
- 栈式
- 标签式

分别使用`$mod+e` `$mod+s` `$mod+w`来选择它们.下面是效果:

![](https://i3wm.org/docs/modes.png)

### 2.3 切换全屏

进入和退出全屏都使用 `$mod+f`.

在i3中还有一个全局全屏模式,其中客户端将跨越所有可用的输出(命令是fullscreen toggle global).

### 2.4 操作其它程序

除了从终端打开程序外,您还可以使用便捷的dmenu，默认情况下按$mod+d打开dmenu.只需键入要打开的程序的名称(或其中的一部分).相应的程序必须在您的$PATH中dmenu才能正常工作.


另外,如果您经常打开应用程序,您可以创建一个键绑定来直接启动应用程序.有关详细信息，请参阅[配置]一节.

> 本身的dmenu并不好用,建议使用rofi.配置在我的配置文件中.

### 2.5 关闭窗口

大多数程序都提供了关闭机制(比如`ctrl+w`).如果没有的话,你可以用`$mod+Shift+q`关闭程序.对于提供了WM_DELETE协议的程序,程序将正确关闭(保存更改或做其他清理).如果没有这种协议的话,你的X server会直接杀死他的进程树.

### 2.6 使用工作区

工作区可以快速的把窗口组分类.默认情况下,你会处于第一个工作区,当前所处位置会在下方的bar中显示.切换工作区可以使用`$mod+num`,如果工作区没有打开,那么它会被打开.

通常情况下,游览器会单独放在一个工作区,通讯程序会在另一个,等等等等.当然你也可以不用这种方式.

如果你使用多屏,工作区会出现在每一块屏幕上.

### 2.7 移动窗口到其他工作区

把焦点放在这个窗口,然后使用`$mod+Shift+num`移动它.如果将去往工作区不存在,他会被创建.

### 2.8 调整大小

调整容器大小最简单的方法是使用鼠标:选中边框并将其移动到需要的大小.你还可以使用[绑定模式]来定义通过键盘调整大小的模式.要查看这方面的示例，请查看i3提供的默认配置.

### 2.9 重启 i3

要在适当的地方重新启动i3(从而在出现bug时进入一个干净的状态,或者升级到一个较新的i3版本)，可以使用`$mod+Shift+r`来重启.

### 2.10 退出 i3

要干净地退出i3而不杀死你的X server,你可以使用`$mod+Shift+e`.默认情况下，会出现一个对话框询问你是否真的想退出.

### 2.11 浮动

浮动式是相对于平铺式来说的.窗口的大小的位置将由你来决定.使用这种模式违反了平铺模式的原则,但是对于某些特殊情况非常有用,比如“另存为”对话框窗口或工具栏窗口(GIMP或类似的程序).这些窗口通常设置适当的提示，并在默认情况下以浮动模式打开.

可以使用`$mod+Shift+Space`切换到浮动模式.左键按住窗口的标签来拖动它.通过选中边框并移动它们,你可以调整窗口的大小.你也可以使用[浮动修饰符](floating modifier)来实现.另一种使用鼠标调整浮动窗口大小的方法是右键单击标题栏并拖动.

浮动窗口将处于平铺窗口的上面.

## 3. 树

i3将有关X11输出、工作空间和窗口布局的所有信息存储在一个树中。根节点是X11根窗口，接着是X11输出，然后停靠区域和内容容器，然后是工作区，最后是窗口本身。在以前的i3版本中，我们为每个工作空间提供了多个列表(输出、工作空间)和一个表。

### 3.1 容器的树状构成

我们树的构件是所谓的容器。容器可以承载一个窗口(意味着一个X11窗口，一个您可以实际查看和使用的窗口，就像浏览器一样)。或者，它可以包含一个或多个容器。一个简单的例子是工作空间:当你用一个显示器开始i3，一个工作空间，你打开两个终端窗口，你会得到一个像这样的树:



![](https://i3wm.org/docs/tree-shot3.png)

![](https://i3wm.org/docs/tree-layout2.png)



### 3.2 定向和拆分容器

为了在使用树作为数据结构时构建布局，使用所谓的分割容器是很自然的。在i3中，每个容器都有一个方向(水平、垂直或未指定的)，方向取决于容器所在的布局(垂直用于splitv和堆叠，水平用于splith和选项卡)。因此，在我们的工作空间示例中，工作空间容器的默认布局是splith(现在大多数监视器都是宽屏的)。如果你把布局改为splitv(默认配置中的$mod+v)，然后打开两个终端，i3会像th一样配置你的窗口

![](https://i3wm.org/docs/tree-shot2.png)

自从版本4以来，i3的一个有趣的新特性就是可以拆分任何东西:假设您的工作空间中有两个终端(使用splith布局，即水平方向)，那么重点是在正确的终端上。现在您希望在当前终端窗口下面打开另一个终端窗口。如果您只是打开一个新的终端窗口，它将显示在右边由于splith布局。相反，按$mod+v以splitv布局拆分容器(要打开水平拆分容器，使用$mod+h)。现在你可以打开一个新的终端，它会在当前终端下面打开:



<img src="https://i3wm.org/docs/tree-shot1.png" style="zoom:%;" />

![](https://i3wm.org/docs/tree-layout1.png)

你可能已经猜到了:分裂等级是没有限制的。

### 3.3 聚焦父窗口

让我们继续上面的例子。我们在左边有一个终端，在右边有两个垂直分开的终端，焦点在右下角。当您打开一个新终端时，它将在当前终端下面打开。

那么，如何在当前终端的右边打开一个新的终端窗口呢?解决方案是使用焦点父容器，它将焦点放在当前容器的父容器上。在默认配置中，使用$mod+a将一个容器导航到树中(您可以重复多次，直到您到达Workspace容器)。在这种情况下，您可以将焦点放在位于水平方向工作区的垂直拆分容器上。因此，现在新的窗口将打开的垂直分裂容器的右边:

![](https://i3wm.org/docs/tree-shot3.png)

### 3.4 隐式容器

在某些情况下，i3需要隐式地创建一个容器来实现您的命令。

一个例子是下面的场景:您使用一个监视器和一个工作区启动i3，在这个工作区上打开三个终端窗口。所有这些终端窗口都直接附加到i3布局树中的一个节点上，即workspace节点。默认情况下，工作空间节点的方向是水平的。

现在将其中一个终端向下移动($mod+Shift+k)。工作空间节点的方向将更改为垂直。您向下移动的终端窗口直接连接到工作区，并出现在屏幕的底部。创建了一个新的(水平)容器来容纳其他两个终端窗口。当切换到选项卡式模式(例如)时，您将注意到这一点。您最终会得到一个带有拆分容器表示的选项卡(例如，“H[urxvt firefox]”)，另一个是向下移动的终端窗口。

## 4. 配置 i3

这是真正的乐趣开始;-)。大多数事情都取决于你理想的工作环境，所以我们不能为它们设置合理的默认值。

虽然没有使用编程语言进行配置，但是i3在您通常希望窗口管理器做的事情方面保持了相当的灵活性。

例如，可以配置绑定来跳转到特定的窗口，可以设置特定的应用程序来启动特定的工作空间，可以自动启动应用程序，可以更改i3的颜色，可以绑定键来做有用的事情。

要更改i3的配置，请将`/etc/i3/config`复制到`~/.i3 /config`，然后用文本编辑器编辑。

在第一次启动时(以及以后的所有启动时，除非您有一个配置文件)，i3将提供您创建一个配置文件。可以告诉向导在配置文件中使用Alt  (Mod1)或Windows  (Mod4)作为修饰符。此外，创建的配置文件将使用当前键盘布局的键符号。要启动向导，请使用命令`i3-config-wizard`。请注意你不能有`~/.i3/config`，否则向导将退出。

从i3 4.0开始，使用了一种新的配置格式。i3会根据一些不同的关键字自动检测配置文件的格式版本，但是如果你想确保你的配置是用新格式读取的，在你的配置文件中包括以下行:

```bash
# i3 config file (v4)
```

### 4.1 注释

您可以使用配置文件中的注释来正确地记录您的设置，以供以后参考。注释以#开头，只能用在一行的开头:

例子:

```bash
# This is a comment
```

### 4.2 字体

i3支持X核心字体和FreeType字体(通过Pango)来呈现窗口标题。

要生成X核心字体描述，可以使用`xfontsel`。要查看特殊字符(Unicode)，您需要使用支持ISO-10646编码的字体。

FreeType字体描述由字体族、样式、重量、变体、延伸和大小组成。FreeType字体支持从右到左的呈现，并且包含的Unicode字形通常比X core字体更多。

 如果i3不能打开配置的字体，它将在日志文件中输出一个错误并退回到工作字体。

格式:

```bash
font <X core font description>
font pango:<family list> [<style options>] <size>
```

例子:

```bash
font -misc-fixed-medium-r-normal--13-120-75-75-C-70-iso10646-1
font pango:DejaVu Sans Mono 10
font pango:DejaVu Sans Mono, Terminus Bold Semi-Condensed 11
font pango:Terminus 11px
```



### 4.3 键盘绑定

键盘绑定使i3在按下特定键时执行命令(见下面)。i3允许您在keycode或keysyms上进行绑定(您也可以混合绑定，尽管i3不能保护您避免绑定的重叠)。

- 一个 keysym(键符号)是对特定符号的描述，如“a”或“b”，但也包括更奇怪的符号。这些是您在Xmodmap中用来重新映射键的。要获得键的当前映射，使用`xmodmap -pke`。要交互式地输入密钥并查看它被配置为什么keysym，可以使用`xev`。
- 键码不需要指定符号(对于某些笔记本上的自定义热键很方便)，而且当您切换到不同的键盘布局时(使用`xmodmap`时)，它们的含义不会改变。

我的建议是:如果您经常切换键盘布局，但希望将绑定保存在键盘上相同的物理位置，那么可以使用keycodes。如果你不想切换布局，想要一个干净简单的配置文件，使用keysyms。

有些工具(如`import`或`xdotool`)可能无法在按键事件上运行，因为键盘/鼠标仍然被抓取。对于这些情况，可以使用`--release`标志，它将在密钥释放后执行命令。

格式:

```bash
bindsym [--release] [<Group>+][<Modifiers>+]<keysym> command
bindcode [--release] [<Group>+][<Modifiers>+]<keycode> command
```

例子:

```bash
# Fullscreen
bindsym $mod+f fullscreen toggle

# Restart
bindsym $mod+Shift+r restart

# Notebook-specific hotkeys
bindcode 214 exec --no-startup-id /home/michael/toggle_beamer.sh

# Simulate ctrl+v upon pressing $mod+x
bindsym --release $mod+x exec --no-startup-id xdotool key --clearmodifiers ctrl+v

# Take a screenshot upon pressing $mod+x (select an area)
bindsym --release $mod+x exec --no-startup-id import /tmp/latest-screenshot.png
```

可接受的修改器:

Mod1-Mod5, Shift,Control.

Group1, Group2, Group3, Group4

​			当使用多个键盘布局(例如setxkbmap -layout  us,ru)时，您可以指定在哪个XKB组(也称为“布局”)中一个键			绑定应该是活动的。默认情况下，密钥绑定在Group1中被转换，并且在所有组中都是活动的。如果希望在			某个布局中覆盖键绑定，请指定相应的组。为了向后兼容，组“模式切换”是Group2的别名。

### 4.4 鼠标绑定

鼠标绑定使i3在单击容器范围内按下特定的鼠标按钮后执行命令(参见[command criteria])。您可以以类似于键绑定的方式配置鼠标绑定。

格式:

```bash
bindsym [--release] [--border] [--whole-window] [--exclude-titlebar] [<Modifiers>+]button<n> command
```

默认情况下，绑定仅在单击窗口标题栏时运行。如果给出了--release标志，它将在释放鼠标按钮时运行。

如果给出了--whole-window标志，那么当单击窗口的任何部分时，绑定也将运行，边界除外。要在单击边框时运行绑定，请指定--border标志。

如果给出了--exclude-titlebar标志，则不会考虑使用titlebar作为键绑定。

例子:

```bash
# The middle button over a titlebar kills the window
bindsym --release button2 kill

# The middle button and a modifer over any part of the window kills the window
bindsym --whole-window $mod+button2 kill

# The right button toggles floating
bindsym button3 floating toggle
bindsym $mod+button3 floating toggle

# The side buttons move the window around
bindsym button9 move left
bindsym button8 move right
```



### 4.5 绑定模式

通过使用不同的绑定模式，可以有多个绑定集。当您切换到另一种绑定模式时，当前模式中的所有绑定将被释放，并且只有在新模式中定义的绑定在您停留在该绑定模式期间有效。唯一预定义的绑定模式是`default`，即i3开始时使用的模式，所有未在特定绑定模式中定义的绑定都属于这个模式。

使用绑定模式包括两部分:定义绑定模式和切换到绑定模式。出于这些目的，有一个配置指令和一个命令，它们都被称为模式。该指令用于定义属于特定绑定模式的绑定，而命令将切换到指定模式。

为了便于维护，建议结合使用绑定模式和[变量]。下面是一个如何使用绑定模式的示例。

注意，最好定义绑定以切换回默认模式。 

请注意，可以将[pango markup]用于绑定模式，但是需要通过将 --pango markup标记传递给模式定义来显式地启用它。

格式:

```bash
# config directive
mode [--pango_markup] <name>

# command
mode <name>
```

例子:

```bash
# Press $mod+o followed by either f, t, Escape or Return to launch firefox,
# thunderbird or return to the default mode, respectively.
set $mode_launcher Launch: [f]irefox [t]hunderbird
bindsym $mod+o mode "$mode_launcher"

mode "$mode_launcher" {
    bindsym f exec firefox
    bindsym t exec thunderbird

    bindsym Escape mode "default"
    bindsym Return mode "default"
}
```



### 4.6 浮动修饰

要用鼠标移动浮动窗口，你可以抓取它们的标题栏，也可以配置所谓的浮动修改器，然后点击窗口中的任何地方来移动它。最常见的设置是使用与管理windows相同的键(例如Mod1)。然后你可以按Mod1，用你的鼠标左键点击进入一个窗口，把它拖到你想要的位置。

当你按住浮动修改器时，你可以通过按住鼠标右键来调整浮动窗口的大小。如果同时按住shift键，则调整大小将成比例(保留长宽比)。

格式:

```bash
floating_modifier <Modifier>
```

例子:

```bash
floating_modifier Mod1
```



### 4.7 限定浮动窗口大小

可以指定浮动窗口的最大和最小尺寸。如果将浮动最大大小的任意维度指定为-1，则该维度的最大值将不受约束。如果未定义或指定为0，则i3将使用默认值来约束最大大小。浮动最小尺寸的处理方式类似于浮动最大尺寸。

格式:

```bash
floating_minimum_size <width> x <height>
floating_maximum_size <width> x <height>
```

例子:

```bash
floating_minimum_size 75 x 50
floating_maximum_size -1 x -1
```



### 4.8 新工作区定位

新工作区有一个合理的默认方向:宽屏显示器(任何比高宽的显示器)有水平方向，旋转显示器(任何比宽宽的显示器)有垂直方向。 

使用默认方向配置指令，您可以覆盖该行为。

格式:

```bash
default_orientation horizontal|vertical|auto
```

例子:

```bash
default_orientation vertical
```

### 4.9 新容器的布局模式

此选项确定工作空间级别上的新容器将以何种模式启动。

格式:

```bash
workspace_layout default|stacking|tabbed
```

例子:

```bash
workspace_layout tabbed
```

### 4.10 窗口标题对齐

此选项确定窗口标题的文本对齐方式。默认是左对齐

格式:

```bash
title_align left|center|right
```

### 4.11 新窗口边框样式

此选项确定新窗口将具有哪些边框样式。默认值为normal。注意，默认的浮动边框只适用于以浮动窗口开始的窗口，例如对话框窗口，而不是以后浮动的窗口。

将边框样式设置为像素可以消除标题栏。边框样式允许你在保持标题栏的同时调整边框宽度。

格式:

```bash
default_border normal|none|pixel
default_border normal|pixel <px>
default_floating_border normal|none|pixel
default_floating_border normal|pixel <px>
```

请注意，新窗口和新浮动已被弃用，以支持上述选项，并将在未来的版本中删除。我们强烈建议使用新选项。

例子:

```bash
default_border pixel
```

“normal”和“pixel”边框样式支持一个可选的像素边框宽度:

例子:

```bash
# The same as default_border none
default_border pixel 0

# A 3 px border
default_border pixel 3
```

### 4.12 隐藏与屏幕边缘相邻的边框

可以使用`hide_edge_borders`隐藏与屏幕边缘相邻的容器边框。如果您正在使用滚动条，或者不希望在显示空间中浪费两个像素，那么这是非常有用的。“智能”设置隐藏了只有一个窗口可见的工作区的边框，但保持了多个窗口可见的工作区的边框。默认是没有的。

格式:

```bash
hide_edge_borders none|vertical|horizontal|both|smart
```

例子:

```bash
hide_edge_borders vertical
```

未完

## 5. 配置 i3bar

显示器底部的条形图是由一个名为i3bar的独立进程绘制的。将“i3用户界面”的这一部分放在单独的进程中有几个优点:

1. 这是一种模块化方法。如果您根本不需要工作空间栏，或者您更喜欢不同的工作空间栏(dzen2、xmobar，甚至gnome-panel?)，那么您可以删除i3bar配置并启动您喜欢的工作空间栏。
2. 它遵循“让每个程序都做好一件事”的UNIX哲学。虽然i3可以很好地管理您的窗口，但i3bar擅长在每个监视器上显示一个栏(除非您另外配置它)。
3. 它导致两个独立的、干净的代码库。如果你想了解i3，你不需要费心去了解i3bar的细节，反之亦然。

也就是说，i3bar是在与i3相同的配置文件中配置的。这是因为它与i3紧密耦合(与i3lock或i3status相反，后者对使用其他窗口管理器的人很有用)。因此，当我们已经有了一个良好的配置基础结构时，使用不同的配置位置是没有意义的。

配置您的工作空间栏首先要打开一个栏块。你可以有多个栏块使用不同的设置为不同的输出(监视器):

例子:

```bash
bar {
    status_command i3status
}
```

### 5.1 i3bar命令

默认情况下，i3只会传递`i3bar`并让您的shell处理执行，在`$PATH`中搜索正确的版本。如果你在某个地方有一个不同的`i3bar`或者二进制文件不在`$PATH`中，你可以告诉i3执行什么。 指定的命令将被传递到`sh -c`，所以您可以使用通配符，并且必须有正确的引用等等。

格式: 

```bash
i3bar_command <command>
```

例子:

```bash
bar {
    i3bar_command /home/user/bin/i3bar
}
```



### 5.2 状态栏命令

3bar可以运行一个程序，并显示其输出的每一行`stdout`在右边的bar。这是有用的显示系统信息，如您的当前IP地址，电池状态或日期/时间。

指定的命令将被传递到sh -c，所以您可以使用通配符，并且必须有正确的引用等等。注意，对于信号处理，根据您的shell(已知dash(1)的用户会受到影响)，您必须使用shell的exec命令，以便将信号传递给您的程序，而不是传递给shell。

格式:

```bash
status_command <command>
```

例子:

```bash
bar {
    status_command i3status --config ~/.i3status.conf

    # For dash(1) users who want signal handling to work:
    status_command exec ~/.bin/my_status_command
}
```



### 5.3 显示模式

你可以让i3bar在屏幕的一边永久可见(dock模式)，也可以让它在你按下修改键(隐藏模式)时显示出来。它也可以强迫i3bar始终保持隐藏(隐形模式)。可以使用`modifier`选项配置`modifier`键。

可以通过bar mode命令在运行时更改模式选项。在重新加载模式将恢复到其配置值。

隐藏模式最大化了可用于实际窗口的屏幕空间。此外，i3bar发送SIGSTOP和SIGCONT信号到statusline进程，以节省电池电力。

隐形模式允许永久最大化屏幕空间，因为该栏从未显示。因此，你可以配置i3bar不打扰你弹出因为一个紧急提示或因为修改键按下。

为了控制i3bar在隐藏模式下是隐藏还是显示，隐藏状态选项是存在的，在dock模式或invisible模式下是无效的。它表明当前的隐藏状态栏:(1)酒吧就像在正常隐藏模式,它是隐藏的,只有进行紧急提示或按修改键(`hide`状态),或(2)画在目前可见的工作区(`show`状态)。

和模式一样，隐藏状态也可以通过i3来控制，这可以通过使用`bar hidden_state`命令来实现。

默认模式为停靠模式;在隐藏模式下，默认的修改器是Mod4(通常是windows键)。隐藏状态的默认值是hide。

格式:

```bash
mode dock|hide|invisible
hidden_state hide|show
modifier <Modifier>|none
```

例子:

```bash
bar {
    mode hide
    hidden_state hide
    modifier Mod1
}
```



### 5.4 鼠标按钮命令

指定当按下i3bar上的按钮以覆盖默认行为时要运行的命令。这很有用,例如为这些按钮添加默认习惯.

一个按钮总是命名为`button<n>`，其中1到5是默认按钮，如下所示，更高的数字可以是设备上提供更多按钮的特殊按钮:

- button1

  ​    Left mouse button.

- button2

  ​    Middle mouse button.

- button3

  ​    Right mouse button.

- button4

  ​    Scroll wheel up.

- button5

  ​    Scroll wheel down.

请注意，我不赞成旧的`wheel_up_md`和wheel_down_cmd命令，并将在未来的版本中删除。我们强烈建议使用带有button4和button5的更通用的bindsym。

格式:

```bash
bindsym [--release] button<n> <command>
```

例子:

```bash
bar {
    # disable clicking on workspace buttons
    bindsym button1 nop
    # Take a screenshot by right clicking on the bar
    bindsym --release button3 exec --no-startup-id import /tmp/latest-screenshot.png
    # execute custom script when scrolling downwards
    bindsym button5 exec ~/.i3/scripts/custom_wheel_down
}
```



### 5.5 Bar ID

指定已配置的bar实例的bar ID。如果缺少此选项，则将ID设置为bar-x，其中x对应于配置文件中嵌入条块的位置(bar-0, bar-1，…)。

格式:

```bash
id <bar_id>
```

例子:

```bash
bar {
    id bar-1
}
```



### 5.6 位置

此选项确定应该显示屏幕i3bar的哪条边。 默认是bottom。

格式:

```bash
position top|bottom
```

例子:

```bash
bar {
    position top
}
```



### 5.7 输出

您可以将i3bar限制为一个或多个输出(监视器)。默认是处理所有输出。限制输出对于通过使用多个bar块为不同的输出使用不同的选项是很有用的。 

要使一个特定的i3bar实例处理多个输出，需要多次指定output指令。

格式:

```bash
output primary|<output>
```

例子:

```bash
# big monitor: everything
bar {
    # The display is connected either via HDMI or via DisplayPort
    output HDMI2
    output DP2
    status_command i3status
}

# laptop monitor: bright colors and i3status with less modules.
bar {
    output LVDS1
    status_command i3status --config ~/.i3status-small.conf
    colors {
        background #000000
        statusline #ffffff
    }
}

# show bar on the primary monitor and on HDMI2
bar {
    output primary
    output HDMI2
    status_command i3status
}
```

注意，您可能还没有配置主输出。为此，运行以下命令:

```bash
xrandr --output <output> --primary
```

### 5.8 托盘输出

i3bar默认提供了一个系统托盘区，在这里，NetworkManager、VLC、Pidgin等程序可以放置小图标。

您可以配置应该显示哪个输出(监视器)图标，也可以完全关闭该功能。 您可以在配置中使用多个tray输出指令来指定您希望tray出现在其上的输出列表。根据指令的顺序定义的列表中第一个可用的输出将用于托盘输出。

格式:

```bash
tray_output none|primary|<output>
```

例子:

```bash
# disable system tray
bar {
    tray_output none
}

# show tray icons on the primary monitor
bar {
    tray_output primary
}

# show tray icons on the big monitor
bar {
    tray_output HDMI2
}
```

注意，您可能还没有配置主输出。为此，运行以下命令:

```bash
xrandr --output <output> --primary
```

请注意，当您使用多个栏配置块时，要么在所有栏中指定`tray_output primary`，要么在不显示tray的栏中明确指定`tray_output none`，否则不同的实例可能会竞相尝试显示tray图标。

### 5.9 托盘边框

托盘在bar的右边。默认情况下，托盘区域的上方、下方和右侧以及各个图标之间使用2像素的内边距。

格式:

```bash
tray_padding <px> [px]
```

例子:

```bash
# Obey Fitts's law
tray_padding 0
```



### 5.10 字体

在bar中使用特殊字体,参见[fonts].

格式:

```bash
font <font>
```

例子:

```bash
bar {
    font -misc-fixed-medium-r-normal--13-120-75-75-C-70-iso10646-1
    font pango:DejaVu Sans Mono 10
}
```



## 6. 命令列表

**待完成**

## 7. 多屏

正如你在网站的目标列表中看到的，i3是专门为支持多显示器而开发的。本节将解释如何处理多个监视器。

 当您只有一个显示器时，事情就很简单了。您通常从显示器上的workspace 1开始，然后根据需要打开新的工作空间。 

当您有多个监视器时，每个监视器将获得一个初始工作区。第一个监视器得到1，第二个得到2，第三个可能得到3。当您切换到另一个监视器上的工作空间时，i3将切换到该监视器，然后切换到工作空间。这样，您就不需要切换到特定监视器的快捷方式，也不需要记住将哪个工作空间放在何处。将在当前活动的监视器上打开新的工作区。没有工作空间就不可能有监视器。

使工作空间全球化的想法是基于这样一种观察:大多数用户在他们的附加监视器上只有非常有限的一组工作空间。它们通常用于特定的任务(浏览器、shell)或监视一些东西(邮件、IRC、syslog……)。因此，在一个监视器上使用一个工作空间，而在其他监视器上使用“rest”通常是有意义的。但是，由于您可以在i3中创建无限数量的工作空间并将它们绑定到特定的屏幕，所以可以采用“传统”方法，即通过更改配置(例如，使用模式)在每个屏幕上创建X个工作空间。

### 7.1 配置你的显示器

如果您以前从未使用过多个监视器，为了帮助您入门，这里简要介绍一下xrandr选项，您可能会对这些选项感兴趣。获得当前屏幕配置的概述总是有用的。只需运行“xrandr”，您将得到如下输出:

```bash
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0
   1024x768       85.0     75.0     70.1     60.0
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
```

这里有几件事很重要:您可以看到LVDS1是连接的(当然，它是内部的平板)，但是VGA1不是。如果你有一个显示器连接到其中一个端口，但xrandr仍然显示“未连接”，你应该检查你的电缆，显示器或图形驱动程序。

在第一行末尾可以看到的最大分辨率是监视器的最大综合分辨率。默认情况下，它通常太低，必须通过编辑`/etc/ x11 /xorg.conf`来增加。 所以，假设你连接了VGA1，并想把它作为一个额外的屏幕:

`xrandr --output VGA1 --auto --left-of LVDS1`

这个命令使xrandr尝试找到连接到VGA1的设备的本机分辨率，并将其配置到内部平板的左侧。再次运行“xrandr”时，输出如下:

```bash
$ xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0
   1280x960       60.0
   1152x864       75.0
   1024x768       75.1     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        72.8     75.0     66.7     60.0
   720x400        70.1
LVDS1 connected 1280x800+1280+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0
   1024x768       85.0     75.0     70.1     60.0
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
```

请注意，i3使用与xrandr完全相同的API，因此它只能看到您在xrandr中看到的内容。 有关多显示器设置的更多示例，请参见[演示文稿]。

### 7.2 多屏的有趣配置

如果你有一个以上的显示器，在i3中有几个配置是很有趣的: 

- 您可以指定应该将哪个工作区放在哪个屏幕上。这允许您在启动时使用一组不同的工作空间，而不只是针对第一个监视器使用1个工作空间，针对第二个监视器使用2个工作空间，以此类推。参见[workspace screen]。
- 如果您希望某些应用程序通常在较大的屏幕上打开(MPlayer、Firefox等)，您可以将它们分配到特定的工作空间，请参见[assign workspace]。
- 如果您在许多监视器上有许多工作空间，那么要跟踪您将哪个窗口放置在何处就比较困难了。因此，您可以使用类似于vm的标记在窗口之间快速切换。参见[vim like marks]。
- 有关如何在监视器之间移动现有工作空间的信息，请参见[move to outputs]。

## 8. i3和软件世界其他事仪

### 8.1 显示状态栏

一个通常的做法是把状态栏放在屏幕某个角落.与传统桌面环境任务栏中的小部件方法相比，它通常是更好的替代方法.

如果你还没有准备好拥有一个可以自动读写,执行脚本的状态栏,那么i3status是一个不错的选择.他是用C语言写的.他的目标是使用尽可能少的系统调用,以减少CPU的使用.由于i3status只负责输出文本.,你还需要组合其他工具一起使用,比如i3bar.关于如何在i3bar中显示i3status可以看[状态命令](#5.2) 未完成❎

无论使用哪个应用程序来显示状态栏,都要确保它使用EWMH提示注册为一个dock窗口.i3将把窗口定位在屏幕的顶部或底部，这取决于应用程序设置.使用i3bar,你可以配置它的位置，详见[i3bar位置]().

### 8.2 多屏

在做演示时，您通常希望观众看到您在屏幕上看到的内容，然后浏览一系列幻灯片(如果演示很简单)。对于更复杂的演示，您可能需要一些只有在屏幕上才能看到的注释，而观众只能看到幻灯片。

#### 8.2.1 情况1: 相同输出

这是一个简单的例子。你把你的电脑连接到视频投影仪，同时打开(电脑和视频投影仪)，并配置你的X服务器把你电脑的内部平板复制到视频输出:

```bash
xrandr --output VGA1 --mode 1024x768 --same-as LVDS1
```

然后i3将使用屏幕分辨率的最低公共子集，您的屏幕的其余部分将保持不变(它将显示X背景)。在我们的例子中，这是1024x768(我的笔记本是1280x800)。

#### 8.2.2 情况2:  你可以看到更多

这种情况有点困难。首先，你应该配置的VGA输出附近的地方，你的内部平板，说它的权利:

```bash
xrandr --output VGA1 --mode 1024x768 --right-of LVDS1
```

现在，i3将在新屏幕上显示一个新的工作空间(取决于您的设置)，您将处于多显示器模式(参见[multi monitor])。

因为i3不是合成窗口管理器，所以无法在两个屏幕上同时显示窗口。相反，您的演示软件需要完成这项工作(即在每个屏幕上打开一个窗口)。

### 8.3 高分辨率(aka HIDPI)

关于在各种各样的Linux 桌面上如何缩放的细节戡夷看这个链接: https://wiki.archlinux.org/index.php/HiDPI 

i3将从Xft.dpi中读取所需的DPI.属性默认为96 DPI,因此要实现200%的缩放,需要设置Xft.dpi: 192dpi的`~ /.xresources`.

如果你使i3的老用户,并且才得到一个新的显示器,只需要两步:

- 在i3的配置中使用一个可以缩放的字体(一开始是`pango`)
- 选择一个可以缩放的终端(比如gnome-terminal),知道你把终端的字体大小调到合适.