# PFWorldReforged
更卓越的Minecraft服务端世界管理系统，全面支持Mohist、CatServer；支持大部分Mod世界

### 使用方法
将PFWR.jar拖入至./plugins文件夹内，并删除原先所有有关世界管理的插件，重启服务端。

### 指令列表
- /pfwr help - 显示帮助界面
- /pfwr world create <名称> <类型> <额外参数> - 创建新世界

> 类型：default（标准世界）；nether（地狱世界）；end（末地世界）
> 额外参数：-g（自定义Generator）；-m（生成该Mod的世界，如果有的话）

- /pfwr world load <名称> - 加载世界
- /pfwr world unload <名称> - 卸载世界
- /pfwr world delete <名称> - 删除世界
- /pfwr world import <名称> <类型> <额外参数> - 导入世界

> 类型：default（标准世界）；nether（地狱世界）；end（末地世界）
> 额外参数：-g（自定义Generator）

- /pfwr world list - 列举所有识别到的世界
- /pfwr world info <名称> - 查看该世界的信息
- /pfwr world setting <名称> <设置内容> - 设置世界的信息

> 设置内容：-difficulty（世界的难度）；-gamemode（世界的游戏类型）；-gamerule（世界的游戏规则）......
> 更多设置内容请在./plugins/PFWR/worlds/世界名称/global.yml中查看并设置

- /pfwr world setspawn <名称> [x] [y] [z] - 设置世界的出生点，x、y、z若不设置，系统会将玩家脚下坐标设置为世界出生点
- /pfwr world setname <世界名称> <世界别名> - 设置世界的别名，支持§转义符、支持papi变量获取、支持中文
- /pfwr world backup <世界名称> <备份名称> - 备份一个世界

- /pfwr teleport <世界名称> <玩家名称> - 将某玩家传送至某世界

### 权限列表
- pfwr.admin（管理员权限，支持所有world子命令）
- pfwr.user（玩家权限，仅支持/ctw teleport与/ctw help，但不建议给予）

### 文件结构
PFWR的文件结构如下表所示
```
./plugins/PFWR
├─ worlds/
│  ├─ 世界名称1/
│  │  ├─ global.yml
|  |  └─ playerdata.yml
│  ├─ 世界名称2/
│  │  ├─ global.yml
|  |  └─ playerdata.yml
│  └─ ...
│
├─ messages/
│  ├─ zh_CN.yml
│  └─ en_US.yml
│
└─ config.yml
```

### config.yml
config.yml通常装有PFWR的全局设置文件

```
# 这里是PFWR的设置文件
# 所有的全局设置都将在这里进行与被识别
# 如需设置某个世界的参数，请前往./plugins/PFWR/worlds/世界名称/global.yml

# 是否启用PFWR
mainfunc_enable=true

# 是否启用Mod支持（纯净服勿开）
forgemode_enable=true

# 是否启用PAPI支持
placeholderAPI_enable=true

# 是否启用玩家数据归档器
playerdata_enable=true

# 备份文件存入硬盘的路径（从./服务端 开始）
backupfile_location=./PFWR/backup

# 备份文件归档类型（.zip、.tar、.gz）
backupfile_function=.zip

# 是否验证世界完整性
research_world=true

# 是否开启rcon控制（不要开启，该功能正在测试中）
rcon_mode=false

# 语言文件类型（zh_CN、en_US等，通常为messages/ 文件夹中的语言文件名称）
language=zh_CN

# 是否开启Mixin模式（纯净服勿开）
mixin_mode=true

# 操作系统类型（Windows请写DOS；macOS、Linux请写UNIX）
system_style=DOS

# 默认的世界Generator（flatworld超平坦、defworld一般类型、airworld虚空；支持插件与Mod的世界Generator）
default_generator=defworld

# 是否开启强制重生模式（慎用，如有CMI、Essentials等基础插件请使用基础插件的重生机制，否则PFWR会强制接管重生机制）
force_respawn=false
```

### global.yml
global.yml通常装有每个世界单独的设置文件

```
# 这里是PFWR的非全局设置文件
# 该设置文件的内容仅会对该世界有影响

# 世界名称
world_name=world

# 世界类型
world_type=default

# 世界Generator
world_generator=defworld

# 世界别名
world_alias=§a主世界

# 以下内容是世界信息参数
world_functions:
    difficulty=EASY
    gamemode=SURVIVAL
    pvp=true
    allowWeather=true
    spawn_animals=true
    spawn_monsters=true
    hunger=true
    autoHeal=true
    keepSpawnInMemory=true
    spawnLocation:
        PFWRWorldSetting:
            x: 0.0
            y: 64.0
            z: 0.0
            pitch: 0.0
            yaw: 0.0
    autoLoad: 'true'
    bedRespawn: 'true'
    playerBlackList:
    - 在这里写黑名单玩家
    seed: 1234567890
    allowFlight=true
```
### zh_CN.yml
这是PFWR的语言文件，英语同理

