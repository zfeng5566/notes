GNU Screen是命令行中终端切换的软件。可以使用Screen创建命令窗口运行任务，切换出去不会终止任务。
>* screen 是一个使用screen创建伪terminal窗口
>* session 表示任务的意思
>* screen session 由Screen创建的任务

正常情况下我们执行一个任务（比如起一个web服务，或者其它执行时间比较长的任务）都需要在一个terminal窗口执行，并且这个窗口不能关闭，如果关闭任务就会终止。使用screen可以分离screen 和 session。让任务后台执行。不用依附terminal窗口。

### 使用 Screen

在一个screen会话窗口下可使用一下快捷键。

| 快捷键       | 描述   |
| --------   | -----  | 
| `ctrl`+`a`+`w`     | 显示所有窗口列表 | 
| `ctrl`+`a`  `ctrl`+`a`    | 切换之前显示的窗口 | 
| `ctrl`+`a`+`c`     | 创建一个新的窗口，并切换到该窗口 |
| `ctrl`+`a`+`n`     | 切换到下一个窗口 | 
| `ctrl`+`a`+`p`     | 切换到上一个窗口 | 
| `ctrl`+`a`+`0-9`     | 切换到窗口0 - 9 | 
| `ctrl`+`a`+`a`     | 发送`ctrl`+`a`到当前窗口 | 
| `ctrl`+`a`+`d`     | **暂时断开screen会话(不会终止任务)**| 
| `ctrl`+`a`+`k`     | 杀死当前窗口| 
| `ctrl`+`a`+`[`     | 进入拷贝/回滚模式| 

#### 常用命令行参数
option:
```shell
screen -a <fileName> 
```
使用一个配置文件代替默认的配置，默认配置文件位于$HOME/.screenrc

```shell
screen -[d|D] [pid.sessionname] 
```
这个命令不是创建新的screen窗口，而是分离其它终端screen任务(即表示关闭任务的scree窗口)。`-d`效果类似在screen窗口中使用`ctrl`+`a`+`d`快捷键命令。`-D`等价于`ctrl`+`a`+`d`,如果没有后台的任务，这个参数将会被忽略。如果和 `-r/-R`参数使用，将会创建一个窗口关联任务。
`-d -r`  如果任务已经从窗口分离，则创建一个窗口管理任务。
```shell
screen -[ls|list]
```
显示所有的任务
```shell
screen -r [pid.sssionname]
```
管理一个已经后台的screen任务,即打开一个终端窗口管理任务.
```shell
screen -S sessionname
```

Options:

|指令|描述|
|---|---|
|-4|            Resolve hostnames only to IPv4 addresses.|
|-6    |        Resolve hostnames only to IPv6 addresses.|
|-a      |      Force all capabilities into each window's termcap.|
|-A -[r\|R]  |   Adapt all windows to the new display width & height.|
|-c file   |    Read configuration file instead of '.screenrc'.|
|-d (-r)   |    Detach the elsewhere running screen (and reattach here).|
|-dmS name  |   Start as daemon: Screen session in detached mode.|
|-D (-r)    |   Detach and logout remote (and reattach here).|
|-D -RR     |   Do whatever is needed to get a screen session.|
|-e xy     |    Change command characters.|
|-f        |    Flow control on, -fn = off, -fa = auto.|
|-h lines   |   Set the size of the scrollback history buffer.|
|-i       |     Interrupt output sooner when flow control is on.|
|-l       |     Login mode on (update /var/run/utmp), -ln = off.|
|-ls [match] |  or|
|-list       |  Do nothing, just list our SockDir [on possible matches].|
|-L          |  Turn on output logging.|
|-Logfile file| Set logfile name.|
|-m           | ignore $STY variable, do create a new screen session.|
|-O           | Choose optimal output rather than exact vt100 emulation.|
|-p window    | Preselect the named window if it exists.|
|-q           | Quiet startup. Exits with non-zero return code if unsuccessful.|
|-Q           | Commands will send the response to the stdout of the querying process.|
|-r [session] | Reattach to a detached screen process.|
|-R           | Reattach if possible, otherwise start a new session.|
|-s shell     | Shell to execute rather than $SHELL.|
|-S sockname  | Name this session <pid>.sockname instead of <pid>.<tty>.<host>.|
|-t title     | Set title. (window's name).|
|-T term      | Use term as $TERM for windows, rather than "screen".|
|-U           | Tell screen to use UTF-8 encoding.|
|-v           | Print "Screen version 4.06.02 (GNU) 23-Oct-17".|
|-wipe [match]| Do nothing, just clean up SockDir [on possible matches].|
|-x           | Attach to a not detached screen. (Multi display mode).|
|-X           | Execute <cmd> as a screen command in the specified session.|

创建一个自定义名字的screen窗口,并打开该窗口。

常用命令
 `screen [commond]`打开一个screen窗口执行shell 命令。

 `screen -S sessionname`打开一个新的窗口并指定会话名。

 `screen -ls` `screen -list`列出所有screen任务。

 在screenc窗口使用`ctrl`+`a`+`d`关闭窗口(任务不终止)。
 
 `screen -r [pid|sessionname]` 打开任务会话窗口。



