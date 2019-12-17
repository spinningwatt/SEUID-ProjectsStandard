# SEUID项目规范

## 概述

本规范针对Unity项目涉及的所有文件。所有规则均严格按照<概述>-<要求>-<禁止>-<示例>的顺序编写。**要求项**使用:star:标识，**禁止项**使用:x:标识。​示例使用引用表示如下:

> 示例块

[TOC]

:chestnut: :o: :x:  :smiley:

## 1. 命名规范

### 1.1 通用命名

所有命名基于以下两种命名规范：

+ PascalCasing
+ camelCasing

PascalCasing 约定每个单词的第一个字符大写（包括超过两个字母的首字母缩写），如以下示例所示：

>```c#
>PropertyDescriptor
>HtmlTag
>```

这里有一种特殊情况，即遇到两个字母的首字母缩略词时，两个字母都要大写，如<kbd>IOStream</kbd>

camelCasing约定将除第一个单词之外的每个单词的第一个字符大写，如以下示例所示。 该示例还显示，以 camelCasing 标识符开始的双字母缩写词都是小写的。

>```c#
>propertyDescriptor
>ioStream
>htmlTag
>```

:star:**要求**：

+ 所有命名必须有意义。
+ 除电子文档外，所有项目文件夹、代码文件、资源文件、代码标识符使用英文单词、英文缩写及数字组合命名。
+ 所有项目文件夹、代码文件命名基于PascalCasing规范。
+ 所有非源码资源文件命名基于camelCasing规范。
+ 命名中若需要分割多个单词组或数字，**仅**使用下划线<kbd>_</kbd>。
+ **电子文档可使用中文命名**，命名格式为<kbd>文件名_YYMMDD_VERSION</kbd>，其中<kbd>YYMMDD</kbd>为6位数日期，<kbd>VERSION</kbd>为两位数版本号，高位补零对齐（用于区分同一文件在同一天内多次修改的副本）。

:x:**禁止**：

+ 所有项目文件夹、电子文档、代码文件、资源文件、代码标识符的命名**禁止**使用<kbd>aaaa.cs</kbd>，<kbd>111.pptx</kbd>等无意义的元素命名。
+ 所有项目文件夹、电子文档、代码文件、资源文件、代码标识符的命名**禁止**出现空格<kbd> </kbd>。
+ 除电子文档外，所有项目文件夹、代码文件、资源文件、代码标识符**禁止**使用中文字符或拼音命名。
+ 除电子文档外，所有代码文件和资源文件**禁止**使用数字后缀区分文件。

对通用命名有以下正确示例：

> ```c#
> xxx项目开题报告_190421.docx		(无同一天内的多个副本则不使用数字后缀)
> xxx使用说明_190514_03.md			(该文件在同一天内的第三份修改存档)
> /Assets/02_Motions/Animations	(项目文件夹命名)
> KeyboardManager.cs				(cs代码文件)
> ui_dateBar_background.png		(资源文件)
> tree_small_trunk.fbx			(资源文件)
> ```



### 1.2 C#代码相关命名

#### 1.2.1 命名空间

以下为命名空间命名的一般规则：

```c#
SEUID.(ProjectName)[.<Feature>][.<Subnamespace>]
```

其中<kbd>SEUID</kbd>为固定名称，表示项目所属为东南大学工业设计系，<kbd>(ProjectName)</kbd>为当前项目名称，方括号<kbd>[]</kbd>内为可选项。

:star:要求：

+ 所有项目代码**必须**有明确的自定义命名空间。
+ 命名空间遵从PascalCasing。

:x:禁止：​

- 不使用下划线、连字符或任何其他非字母数字的字符。
- 命名空间下的类名不可和该命名空间重名。

命名空间命名有以下正确示例：

> ```c#
> SEUID.JTZKGesture				(命名空间至少含有项目名)
> SEUID.JTZKGesture.HMM.Core		(后续命名可选)
> ```



#### 1.2.2 类、结构体、接口及成员

:star:要求：

+ 遵从PascalCasing规范。
+ 类、结构体的命名请使用**名词性**单词。
+ 接口命名请务必以大写字母<kbd>I</kbd>作为前缀，并使用**描述性名词**或**形容词**。
+ 成员方法命名请使用**动词性短语**或**动宾短语**。
+ 属性名称必须**名词短语**或**形容词**。
+ 事件名称使用**动词短语**命名。
+ 属性、字段若为布尔值，请考虑使用<kbd>Is</kbd>、<kbd>Can</kbd>或<kbd>Has</kbd>等表示是否的前缀。
+ 属性所封装的私有字段请考虑使用下划线<kbd>_</kbd>做前缀，后跟属性名。
+ 事件命名请考虑使用<kbd>On</kbd>前缀或<kbd>Has-Done</kbd>的形式。

:x:禁止：

+ 为类名，结构体名添加前缀。
+ 字段名称不可为**动词性**短语。

命名有以下正确示例：

> ```c#
> Person									(类名)
> RadarData								(结构体名)
> ILinkable								(接口名)
> public void CountCentrePoint			(方法名)
> private int _Age						(字段名)
> public int Age							(属性名)
> protected bool IsActive					(bool字段名)
> public bool CanTouch					(bool字段名)
> public UnityEvent HasEnterProtectedZone	(事件名)
> public UnityEvent OnTouchNode			(事件名)
> ```



#### 1.2.3 .cs文件

:star:要求：

+ 遵从PascalCasing规范
+ 文件名与脚本中主要类名一致。

:x:禁止：

+ **不可**使用数字前缀或后缀区分源码文件。

.cs文件命名有以下正确示例：

> KeyboardManager.cs
> PositionClipNode.cs



### 1.3 Unity项目相关命名

#### 1.3.1 项目文件夹

:star:要求：

+ 一个文件夹下应**只包含一种文件**，按照文件类型分类。

项目文件夹命名有以下正确示例：

> +Textures			(Textures文件夹下全为纹理文件夹或文件)
> |----Trees
> |----Rockets
> |----background_island_AO.png
>
> Models					(Models文件夹下全为模型文件夹或文件)
> |----J20
> |----Carrier
> |----player.fbx



#### 1.3.2 非源码资源

:star:要求：

+ 为形成大小类型的包含关系，使用下划线<kbd>_</kbd>做分割。
+ 文件名中单词顺序应从大类向小类排列。
+ 同一大类资源的不同文件命名应使用**形容词性**或**状态、动作描述性**的后缀。
+ 仅在形容词性后缀不足以区分时，添加两位数字作为后缀，并在高位补零对齐。

:x:禁止：

+ **禁止**使用前缀区分同一大类下的不同文件，前缀区分会导致文件排序混乱。

非源码资源命名有以下正确示例：

> +Models
> |----tree_small_trunk.fbx
> |----tree_small_leaves.fbx
> |----tree_small_roots.fbx				(从大到小做分类命名)
>
> vehicle_truck_damaged.anim
> vehicle_truck_normal.anim			(使用形容词性的后缀区分)
> vehicle_truck_run_01.anim
> vehicle_truck_run_02.anim			(添加两位数字后缀区分)



## 2. 代码规范

###　2.1 布局规范

### 2.2 注释规范

## 3. Unity项目规范

### 3.1 目录结构规范

### 3.2 Scene Hierarchy规范

### 3.3 工作流规范

