# Swar's Chia Plot Manager 粉丝版本翻译（已升级 0.1.0）
 
下载或者查看英文请到原地址：https://github.com/swar/Swar-Chia-Plot-Manager

这是我为它制作的视频：https://www.youtube.com/watch?v=CJcVSzpaXLQ&t=1715s

>请注意，我并不以此牟利，不求任何人的关注，做影片完全是出于锻炼自己的目的，我志远不在此。

它是一个 chia 的绘图管理器 
 

![The view of the manager](https://i.imgur.com/SmMDD0Q.png "View")

开发版本：v0.0.1

这是一个跨平台的 Chia  绘图管理器，可以在主流的操作系统上工作。它不是用来绘图的。绘图还是 chia 做的事情，这个库的目的是管理你的 chia 尽兴绘图，并使用你配置的 config.yaml 置来启动新的绘图。每个人的系统都不尽相同，所以定制是这个库中的一个重要特征（编写大家自己的 config.yaml）。

这个库很简单，易于使用，而且可靠，可以保持绘图的生成。

这个库已经在 Windows 和 Linux 上进行了测试，我本人（卧底小哥）在 mac 和 windows 上进行了测试

## 特点

错开你的绘图，这样你的计算机资源就可以避免高峰期。
允许一个目标目录列表。
通过交错时间提前启动一个新的绘图，最大限度地利用临时空间。
同时运行最大数量的绘图，以避免瓶颈或限制资源占用。
更深入的检测绘制过程。
 
## 支持/问题

请不要使用GitHub问题来提问或支持你自己的个人设置，问题应该与代码错误有关，因为它已经被许多人测试过，可以在 Windows、Linux 和 Mac OS 上工作。因此，任何与技术支持、配置设置有关的问题，或者与你自己的个人使用情况有关的问题，都应该在下面的任何一个链接中提问。

Discord：[https://discord.gg/XyvMzeQpu2](https://discord.gg/XyvMzeQpu2)
这是官方 Discord 服务器 - Swar's Chia 社区

官方Chia Keybase团队：[https://keybase.io/team/chia_network.public](https://keybase.io/team/chia_network.public)频道是#swar

GitHub讨论区: [https://github.com/swar/Swar-Chia-Plot-Manager/discussions](https://github.com/swar/Swar-Chia-Plot-Manager/discussions)


## 常见的问题


**我可以重新加载我的配置吗？**
- 是的，你的配置可以通过`python [manager.py](http://manager.py/) restart`命令来重新加载，或者单独停止并重新启动管理器。请注意，你的任务数将被重置！临时目录2和目标目录的顺序也将被重置。

- 请注意，如果你改变了任务的任何一个目录，它将扰乱现有的任务，管理器和视图将无法识别旧的任务。如果你在有活动绘图的情况下改变任务目录，请将当前任务的 `max_plots` 改为0，然后用新目录做一个单独的任务。我不建议在计划运行时改变目录。

**如果我停止绘图器，是否会杀死我的任务？**
- 不会，绘图是在后台启动的，它们不会杀死你现有的绘图。如果你想结束它们，你可以访问PIDs，并手动结束它们。请注意，你还必须删除.tmp文件。我不为你处理这个问题。

**如果我有一个列表，如何选择`temporary2`和目的地？**

- 它们是按顺序选择的。如果你有两个目录，第一个绘图会选择第一个，第二个会选择第二个，而第三个会选择第一个,这样循环 1 2 1 2 1 2 1...

**什么是 temporary2_destination_sync？**

一些用户喜欢选择总是拥有相同的`temporary2`和目标目录。启用这个设置将总是让 `temporary2` 作为目的地的磁盘。如果你使用这个设置，你可以使用一个空的 `temporary2` ]

**对我的设置来说，什么是最好的配置？**

- 请把这个问题转发给 `Keybase` 或在 github 添加讨论标签。



## 所有命令

##### 命令的使用实例
```文字
> python3 manager.py start

> python3 manager.py 重新启动

> python3 manager.py stop

> python3 manager.py view

> python3 manager.py status

> python3 manager.py analyze_logs
```

### start

这个命令将在后台启动管理器。一旦你启动它，它就会一直运行，除非所有的作业都完成了`max_plots` 或者出现了错误。错误将被记录在一个创建的`debug.log`文件中。

### stop

这个命令将在后台终止管理器，它不会停止运行中的绘图，只会停止新绘图的创建。

### restart

该命令将依次运行启动和停止。

### view

该命令将显示你可以用来跟踪你正在运行的绘图的视图。这将在你的`config.yaml'中定义的每X秒更新一次。

### status

该命令将对视图进行一次快照,它不会循环。

### analyze_logs

该命令将分析你的日志文件夹中所有完成的绘图日志，并为你的计算机配置计算适当的权重。只需在你的`config.yaml`中的`progress`部分填入返回的值。这只影响进度条。


## 安装

这个库的安装是很简单的。我在下面附上了详细的说明：

1、下载并安装Python 3.7或更高版本：[https://www.python.org/](https://www.python.org/)

2、`git clone` 命令克隆这个库或者直接网页下载它（download zip）。

3、打开 CommandPrompt / PowerShell / Terminal，等任何命令行工具，然后 `cd` 到主库文件夹。

- 例如：`cd C:\Users\Swar\Documents\Swar-Chia-Plot-Manager`

4、可选：为Python创建一个虚拟环境。如果你用Python做其他事情，建议这样做：

- 创建一个新的 `Python` 环境： `python -m venv venv`

- 第二个venv可以重命名为你想要的任何东西。作者更喜欢用venv，因为它是一个规范。

- 激活这个虚拟环境。每次打开新窗口时都必须这样做。
    -  Windows：`venv\Scripts\activate`
    -  Linux: `./venv/bin/activate` 或 `source ./venv/bin/activate`

- 通过看到(venv)的前缀来确认它已经激活了，前缀会根据你给它起的名字（venv）而改变。

5、安装所需模块： `pip install -r requirements.txt`

6、在同一目录下复制 `config.yaml.default` 并命名为 `config.yaml`

7、按照你自己的个人设置编辑和设置`config.yaml` 下面有更多关于这方面的帮助

- 你还需要添加 `chia_location!` 这应该指向你的chia可执行文件（注意这个不是环境变量，这个工具不需要你配置环境变量）

8、运行管理器： `python manager.py start`

- 这将在后台启动一个进程，根据你输入的设置来管理绘图。

9、运行视图： `python manager.py view`

- 这将循环查看检测屏幕上的正在活动地块的详细信息。

## 配置

这个库的配置对每个终端用户都是独一无二的 `config.yaml` 文件是配置的所在。

这个绘图管理器是基于任务的概念来工作的。每个任务都有自己的设置，你可以对每个任务进行个性化设置，没有哪个是唯一的，所以这将为你提供灵活性。

### chia_location

这是一个变量，每个人可能都是不一样的，应该包含你的 `chia` 可执行文件的位置。这就是 chia 的可执行文件。

- Windows的例子：`C:\Users\你的用户名\AppData\Local\chia-blockchain\app-你的chia版本\resources\app.asar.unpacked\daemon\chia.exe`

- Linux的例子: `/usr/lib/chia-blockchain/resources/app.asar.unpacked/daemon/chia`

- 另一个Linux例子: `/home/swar/chia-blockchain/venv/bin/chia`

### 管理

这些是只由绘制管理器使用的配置设置。

- `check_interval` - 在检查是否有新任务开始之前的等待秒数。

- `log_level` - 保持在 ` ERROR ` 上，只在有错误时记录。把它改为 `INFO`，以便看到更详细的日志记录。警告:`INFO` 会写下大量的信息。

### 日志

- `folder_path` - 这是你的日志文件的文件夹，用于保存绘图。

### 视图

这些是视图将使用的设置

- `check_interval` - 更新视图前的等待秒数。
- `datetime_format` - 视图中希望显示的日期时间格式。格式化见这里：[https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
- `include_seconds_for_phase` - 时间转换格式是否包括秒。
- `include_drive_info` - 是否会显示驱动器相关信息。
- `include_cpu` - 是否显示CPU的相关信息。
- `include_ram` - 是否显示RAM的相关信息。
- `include_plot_stats` - 是否会显示绘图统计相关信息。
### 通知
这些是不同的设置，以便在绘图管理器启动和绘图完成时发送通知。

### 进度
- `phase_line_end` - 这些设置将用于决定一个阶段在进度条中的结束时间。它应该反映出该阶段结束的线，这样进度计算就可以使用该信息与现有的日志文件来计算进度百分比。
- `phase_weight` - 这些是在进度计算中分配给每个阶段的权重,通常情况下，第1和第3阶段是最长的阶段，所以它们将比其他阶段拥有更多的权重。

### 全局
- `max_concurrent` - 你的系统可以运行的最大绘图数量,管理器在一段时间内启动的地块总数不会超过这个数量。
- `max_for_phase_1` - 系统在第一阶段可以运行的最大绘图数量。
- `minimum_minutes_between_job` - 开始一个新的绘图任务前的最小分钟数，这可以防止多个工作在同一时间开始，这将缓解目标磁盘的拥堵，设置为0表示禁用。

## 任务
- 这些是每个任务使用的设置，请注意，你可以有多个任务，每个任务都应该是YAML格式的，这样才能正确配置。这里几乎所有的值都将被传递到Chia可执行文件中。

点击这里参考更多关于Chia CLI的详情：[https://github.com/Chia-Network/chia-blockchain/wiki/CLI-Commands-Reference](https://github.com/Chia-Network/chia-blockchain/wiki/CLI-Commands-Reference)

- `name` - 这是你要给的名字。
- `max_plots` - 这是在管理器的一次运行中，任务的最大数量。任何重新启动管理器的操作都会重置这个变量，它在这里只是为了帮助你在这段时间内的绘图。
- [OPTIONAL] `farmer_public_key` - 你的chia耕种公钥。如果没有提供，它将不会把这个变量传给chia执行程序，从而导致你的默认密钥被使用。只有当你在一台没有你的证书的机器上设置了chia时才需要这个。
- [OPTIONAL] `pool_public_key` - 你的池公钥。与上述信息相同。
- `temporary_directory` - 这里应该只传递一个目录。这是将进行绘图的地方。
- [OPTIONAL]`temporary2_directory `- 可以是一个单一的值或一个值的列表。这是一个可选的参数，如果你想使用 Chia 绘图的 temporary2 目录功能，可以使用这个参数。
- `destination_directory` - 可以是一个单一的值或一个值的列表。这是绘图完成后将被转移到的最终目录。如果你提供一个列表，它将逐一循环浏览每个磁盘。
- `size` - 这指的是绘图的k大小。你可以在这里输入32、33、34、35......这样的内容（这取决于你之前的习惯）
- `bitfield` - 这指的是你是否想在你的绘图中使用`bitfield`通常情况下，推荐使用 `true`
- `threads` - 这是将分配给 plot 绘图的线程数。只有第1阶段使用1个以上的线程。（这里尤为注意，这是每个绘图任务的线程，对应 chia 官方的 2 自行改动）
- `buckets` - 要使用的桶的数量。Chia提供的默认值是128。
- `memory_buffer` - 你想分配给进程的内存数量。
- `max_concurrent` - 这个任务在任何时候都要有的最大数量的绘图。
- `max_concurrent_with_start_early` - 这项工作在任何时候拥有的最大绘图数量，包括提前开始的阶段。
- `stagger_minutes` - 每个任务并发之间的交错时间单位 分钟。如果你想让你的 plot 在并发限制允许的情况下立即被启动，你甚至可以把它设置为零（为 0 就是同步开始，没有交错时间，不推荐设置为0，最佳 stagger 一般是平均速度的 1/6为最佳，这是我在 reddit 看到的测试）
- `max_for_phase_1` - 这个任务在第1阶段的最大绘图数量。
- `concurrency_start_early_phase` - 你想提前启动一个绘图的阶段。建议使用4。
- `concurrency_start_early_phase_delay` - 当检测到提前开始阶段时，在新的绘图被启动之前的最大等待分钟数。 

- `temporary2_destination_sync` - 这个字段将始终提交目标目录作为临时2目录。这两个目录将是同步的，因此它们将总是以相同的值提交。

- `exclude_final_directory` - 是否为收个几跳过最终目录

- `destination_directory`进行耕作，（这是Chia的一个功能）
- `skip_full_destinations` - 启用该功能时，它将计算所有正在运行的 plot 和未来 plot 的大小，以确定磁盘上是否有足够的空间来启动任务，如果没有，它将跳过该磁盘，转到下一个，一旦所有的空间都满了，它就会停用作业。
- `unix_process_priority` - 仅限UNIX操作系统，这是 plot 生成时将被赋予的优先级。UNIX值必须在-20和19之间。该值越高，进程的优先级越低。
- `windows_process_priority` - 仅限Windows操作系统，这是 plot 在生成时将被赋予的优先级。Windows的数值不同，应该设置为以下数值之一。
	- 16384 `below_normal_priority_class`（低于正常优先级）。
	- 32 `normal_priority_class`（正常优先级）。
	- 32768 "高于正常优先级"。
	- 128 "高优先级 "的
	- 256 "实时优先级"。
- `enable_cpu_affinity` - 启用或禁用绘图进程的 cpu 亲和性，绘图和收割的系统在排除一个或两个线程的绘图进程时，可能会看到收割机或节点性能的改善。
- `cpu_affinity` - 为绘图进程分配的cpu（或线程）的列表。默认例子假设你有一个超线程的4核CPU（8个逻辑核心）。这个配置将限制绘图进程使用逻辑核心0-5，把逻辑核心6和7留给其他进程（6个使用（限制6个），2个空闲）。
