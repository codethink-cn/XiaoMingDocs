### XiaoMingMinecraft
# 小明 Minecraft 互通插件

本插件是运行在 `Bukkit`、`Spigot`、`Paper`、`Pupur`、`Bungee（即将发布）` 等端的 `Minecraft` 服务器 - `QQ` 互通插件。

项目基于小明 `QQ` 机器人框架 [XiaoMingBot](https://github.com/XiaoMingProject/XiaoMingBot) 开发，项目地址：[XiaoMingMinecraft](https://github.com/Chuanwise/XiaoMingMinecraft)

除了支持最基础的远程执行指令、绑定查询、互通聊天外，本插件还支持跨区域 @、申请执行指令等功能。

**小明及相关插件的技术交流 / 用户 QQ 群 `小明练剑场`** ：[`1028959718`](https://jq.qq.com/?_wv=1027&k=sjBXo6xh)

## 快速开始
### 配置小明
请参照 [用户手册](http://chuanwise.cn:10074/#/manual) 的内容启动 `XiaoMingHost`。

### 让小明连接服务器
关闭小明后，在小明练剑场群中下载到 `XiaoMingMinecraft` 插件，将它放入 `Bukkit 1.7` 或更高版本的服务器后台（是，你没看错，小明支持 `1.7`）**和** `小明根目录/plugins/` 下。随后分别重启或启动 `Minecraft` 服务器和小明。

**务必注意，`MC` 服务器后台的 `plugins` 和 `小明根目录/plugins` 都要放！两边都要装！！！！！**

**务必注意，`MC` 服务器后台的 `plugins` 和 `小明根目录/plugins` 都要放！两边都要装！！！！！**

**务必注意，`MC` 服务器后台的 `plugins` 和 `小明根目录/plugins` 都要放！两边都要装！！！！！**

小明默认占用的端口是 `23333`。如果该端口没有占用，启动小明时你将看到如下输出：

```log
[2022-01-07 00:45:16] [main] [INFO]  PluginManagerImpl : 正在启动插件：XiaoMingMinecraft
[2022-01-07 00:45:16] [nioEventLoopGroup-3-1] [INFO]  XiaoMingMinecraft : 成功在端口 23333 上启动服务器
```

如果此时没有成功在端口 `23333` 上启动服务器，请查看 [修改端口的方式](#修改端口的方式) 中有关修改端口的描述。

#### `Minecraft`服务器和小明在同一台设备上
如果 `Minecraft` 服务器和小明在同一台设备上，小明和服务器初始情况下会自动连接，但小明会拒绝连接。

你将在 `Minecraft` 服务器后台看到如下输出：

```log
[00:46:01] [nioEventLoopGroup-2-1/INFO]: [小明] 成功连接到小明
[00:46:01] [nioEventLoopGroup-2-2/INFO]: [小明] 未成功通过验证，请先私聊小明「迎接新服务器」后使用 /xm connect 再次尝试
```

你将在 `小明控制台` 看到如下输出：

```log
[2022-01-07 00:46:01] [nioEventLoopGroup-3-3] [INFO]  XiaoMingMinecraft : 陌生服务器连接到小明，但因为尚未开启迎新模式，故被拒绝连接
```

请按照提示操作。私聊机器人的 `QQ` 号，发送 `迎接新服务器`，随后在 `Minecraft` 服务器后台输入 `xm connect` 重新连接。你将在后台看到连接验证码，将它发送给小明，并给服务器起一个名字，即可完成初次连接。

> 现在你已经完成初次连接，接下来请阅读 [配置互通频道](#配置互通频道)

#### `Minecraft`服务器和小明不在同一台设备上
如果 `Minecraft` 服务器和小明不在同一台设备上，则数据需要走公网。

请参照 [修改主机的方式](#修改主机的方式) 将 `Minecraft` 那边的 `XiaoMingMinecraft` 要连接主机设置为小明所在的主机地址。

如果小明所在的主机的 `23333` 端口是开放的，并且小明成功在该端口上启动服务器，则不需要修改端口，否则请参照 [修改端口的方式](#修改端口的方式) 修改端口。

随后在 `Minecraft` 服务器上执行 `xm connect` 让小明再次连接。**如果连接失败，请检查防火墙或云主机入出方向规则**。如果连接成功，请参照 [`Minecraft`服务器和小明在同一台设备上](#`Minecraft`服务器和小明在同一台设备上) 的方式继续连接。

> 现在你已经完成初次连接，接下来请阅读 [配置互通频道](#配置互通频道)

#### 修改端口的方式
**除非你知道你正在干什么，否则请勿擅自修改端口**

如果已经成功在现有端口上开启服务器，请先执行小明指令 `关闭服务器`。

随后执行小明指令 `设置服务器端口  [新端口值]`，例如 `设置服务器端口  23334`。随后发送 `关闭服务器` 和 `启动服务器`。小明将在新的端口上开启服务器。

如果小明回复启动失败，则可能是端口被占用，重新设置一个新的端口再次启动服务器即可。

随后请在 `Minecraft` 服务器后台执行 `xm config port [新端口值]`，例如 `xm config port 23334`。

#### 修改主机的方式
**除非你知道你正在干什么，否则请勿擅自修改主机**

请在 `Minecraft` 服务器后台执行 `xm config host [主机地址]`，例如 `xm config port 127.0.0.1`。

### 配置互通频道
#### 基础知识
你可以执行小明指令 `指令格式  XiaoMingMinecraft` 显示插件的所有指令，也可以通过 `查指令  [关键字]` 搜索相关指令。

小明的指令过多，大都见名知意，不一一介绍。

#### 快速互通向导
执行小明指令 `双向聊天频道向导`，按照指示即可快速创建双向互通的聊天频道。

#### 自定义互通
自定义互通，你需要了解四个基本组件：

##### 触发器
**触发器是当某些事件发生时会产生消息的组件**。如果你有编程基础，很容易意识到这就是事件监听器。

例如，服务器玩家死亡时触发**玩家死亡触发器**，玩家上线时触发**玩家上线触发器**。`QQ` 上也类似，群聊中出现新消息时触发**群聊消息触发器**，对 `Bot` 的私聊中出现新消息时触发**私聊消息触发器**。

显然触发器可分成两大类：**QQ 触发器** 和 **服务器触发器**。

触发器触发后，会产生一些变量，用于执行相关操作。欲了解更多信息，请查看 [触发器变量表](#触发器变量表)。

##### 执行器
**执行器是进行某些操作的组件**。例如，**群聊广播执行器**可以将特定消息发送到一些群中，**私聊广播执行器**可以将特定消息私聊发送给一些用户。

执行器执行时一些参数将从触发器的变量中获取。例如，你可以要求群聊广播执行器发送 `你好，{sender}` 消息，其中的 `{sender}` 变量就是从前面的触发器中获取的。

##### 工作组
**工作组是为完成特定功能的触发器和执行器组合**。

例如，需要在玩家加群时进行以下操作：

1. 在所有服务器广播 `欢迎 XXX 加入服务器群！`
1. 向该成员发送 `欢迎加入服务器群！`

那么这些功能的组合顺序就是：`成员入群触发器` -> `服务器广播执行器` -> `回复执行器`。这条链以触发器开头，后面为一些执行器。这就是一个工作组。

工作组带有名字，可以被安装到**频道**上。

##### 频道
**频道是一些工作组的集合**。频道可以开关，关闭时所有工作组皆被关闭。建议一个频道对应一个服务器。

该功能对多服务器用户而言非常有用，当某个服务器维护时，就可以关闭对应的频道，避免玩家执行操作。

## 高级配置
### 触发器变量表
所有的触发器都具备小明内核的变量，以及：

|变量名|值|类型|说明|
|---|---|---|---|
|`channel`|触发器所在的频道|`PlayerInfo`|
|`workGroup`|触发器所在的工作组|`WorkGroup`|
|`trigger`|触发器自身|`Trigger<?>`|

此外，每一种触发器还具备下列变量：

#### 群聊消息触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`player`|该 `QQ` 绑定的玩家信息|`PlayerInfo`|如果没有绑定则无此变量|
|`playerOrName`|该 `QQ` 的默认玩家名（绑定时）或备注（未绑定时）|`String`|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`sender`|消息发送者|`XiaoMingUser`||
|`user`|消息发送者|`XiaoMingUser`|和 `sender` 等价|
|`contact`|群聊会话|`GroupXiaoMingContact`|和 `{user.contact}` 等价|
|`groupTag`|激活该触发器所需的群聊标签|`String`|
|`groupCode`|群号|`long`|和 `{user.contact.code}` 等价|

#### 私聊消息触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`player`|该 `QQ` 绑定的玩家信息|`PlayerInfo`|如果没有绑定则无此变量|
|`playerOrAlias`|该 `QQ` 的默认玩家名（绑定时）或备注（未绑定时）|`String`|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`sender`|消息发送者|`XiaoMingUser`||
|`user`|消息发送者|`XiaoMingUser`|和 `sender` 等价|
|`contact`|群聊会话|`PrivateXiaoMingContact`|和 `{user.contact}` 等价|

#### 服务器玩家聊天触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`server`|服务器信息|`ServerInfo`||
|`serverTag`|激活该触发器所需的服务器标签|`String`|如果没有设置则无此变量|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`player`|消息发送者|`String` 或 `PlayerInfo`|若绑定则为 `PlayerInfo`，否则为玩家名|
|`sender`|消息发送者|`XiaoMingUser`|和 `player` 等价|
|`playerOrAlias`|该玩家绑定的 `QQ` 的备注（绑定时）或玩家名（未绑定时）|`String`|
|`message`|聊天信息|`String`||

#### 服务器玩家切换世界触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`server`|服务器信息|`ServerInfo`||
|`serverTag`|激活该触发器所需的服务器标签|`String`|如果没有设置则无此变量|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`player`|消息发送者|`String` 或 `PlayerInfo`|若绑定则为 `PlayerInfo`，否则为玩家名|
|`sender`|消息发送者|`XiaoMingUser`|和 `player` 等价|
|`playerOrAlias`|该玩家绑定的 `QQ` 的备注（绑定时）或玩家名（未绑定时）|`String`|
|`fromWorld`|切换自世界的名字|`String`||
|`toWorld`|切换到世界的名字|`String`||

#### 服务器玩家死亡触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`server`|服务器信息|`ServerInfo`||
|`serverTag`|激活该触发器所需的服务器标签|`String`|如果没有设置则无此变量|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`player`|消息发送者|`String` 或 `PlayerInfo`|若绑定则为 `PlayerInfo`，否则为玩家名|
|`sender`|消息发送者|`XiaoMingUser`|和 `player` 等价|
|`playerOrAlias`|该玩家绑定的 `QQ` 的备注（绑定时）或玩家名（未绑定时）|`String`|
|`message`|死亡信息|`String`||

#### 服务器玩家上线触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`server`|服务器信息|`ServerInfo`||
|`serverTag`|激活该触发器所需的服务器标签|`String`|如果没有设置则无此变量|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`player`|消息发送者|`String` 或 `PlayerInfo`|若绑定则为 `PlayerInfo`，否则为玩家名|
|`sender`|消息发送者|`XiaoMingUser`|和 `player` 等价|
|`playerOrAlias`|该玩家绑定的 `QQ` 的备注（绑定时）或玩家名（未绑定时）|`String`|
|`message`|上线信息|`String`||

#### 服务器玩家下线触发器
|变量名|值|类型|说明|
|---|---|---|---|
|`server`|服务器信息|`ServerInfo`||
|`serverTag`|激活该触发器所需的服务器标签|`String`|如果没有设置则无此变量|
|`accountTag`|激活该触发器所需的用户标签|`String`|如果没有设置则无此变量|
|`mustBind`|是否必须绑定玩家名才能激活该触发器|`boolean`||
|`xiaoMingPermission`|激活该触发器所需的小明权限|`String`|如果没有设置则无此变量|
|`playerPermission`|激活该触发器，所绑定的玩家名至少要有的权限|`String`|如果没有设置则无此变量|
|`player`|消息发送者|`String` 或 `PlayerInfo`|若绑定则为 `PlayerInfo`，否则为玩家名|
|`sender`|消息发送者|`XiaoMingUser`|和 `player` 等价|
|`playerOrAlias`|该玩家绑定的 `QQ` 的备注（绑定时）或玩家名（未绑定时）|`String`|
|`message`|下线信息|`String`||

### 类型运算
#### 频道 `Channel`
|运算|类型|说明|
|---|---|---|
|`name`|`String`|频道名|
|`enabled`|`boolean`|频道是否开启|
|`workGroups`|`Map<String, WorkGroup>`|工作组|

#### 工作组 `WorkGroup`
|运算|类型|说明|
|---|---|---|
|`trigger`|`Trigger<?>`|触发器|
|`executors`|`List<Executor>`|执行器|

#### 触发器 `Trigger`
|运算|类型|说明|
|---|---|---|
|`type`|`String`|触发器类型|

#### 玩家信息 `PlayerInfo`
|运算|类型|说明|
|---|---|---|
|`names`|`List<String>`|玩家名|
|`name`|`String`|默认玩家名（第一个玩家名）|
|`codes`|`Set<Long>`|玩家 `QQ`|

#### 服务器信息 `ServerInfo`
|运算|类型|说明|
|---|---|---|
|`name`|`String`|服务器名|

## 开发文档
如你希望将 `XiaoMingMinecraft` 作为依赖加入 `Maven` 项目中，请在 `pom.xml` 中引用椽子 `Maven` 中央仓库：

```xml
<repositories>
    <!-- chuanwise's maven center -->
    <repository>
        <id>chuanwise-maven</id>
        <url>https://maven.chuanwise.cn</url>
    </repository>
</repositories>
```

随后添加 `XiaoMingMinecraft` 依赖：

```xml
<dependencies>
    <!-- xiao ming minecraft -->
    <dependency>
        <groupId>cn.chuanwise</groupId>
        <artifactId>XiaoMingMinecraft</artifactId>
        <version>5.0.2-SNAPSHOT</version>
        <!-- provided or compile -->
        <scope>provided</scope>
    </dependency>
</dependencies>
```

这里面的版本号 `5.0.2-SNAPSHOT` 不一定是最新的（文档偶尔才更新），最新版本号和小明练剑场群文件中的相同。

`scope` 不一定是 `provided`，请根据需要修改。

写好之后，你的 `pom.xml` 应该看起来像是这样：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>cn.chuanwise.xiaoming</groupId>
    <artifactId>XiaomingMinecraft</artifactId>
    <packaging>pom</packaging>
    <version>2.2</version>

    <repositories>
        <!-- chuanwise's maven center -->
        <repository>
            <id>chuanwise-maven</id>
            <url>https://maven.chuanwise.cn</url>
        </repository>
    </repositories>

    <dependencies>
        <!-- xiao ming minecraft -->
        <dependency>
            <groupId>cn.chuanwise</groupId>
            <artifactId>XiaoMingMinecraft</artifactId>
            <version>5.0.2-SNAPSHOT</version>
            <!-- provided or compile -->
            <scope>provided</scope>
        </dependency>
    </dependencies>
</project>
```

刷新 `Maven`，即可使用 `XiaoMingMinecraft` 的 `API`。