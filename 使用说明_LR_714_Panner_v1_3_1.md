# LR_714_Panner_v1_3_1 使用说明

版本：Public Beta 1.3.1  
设备类型：Max for Live Audio Effect  
用途：在 Ableton Live 中把一条音频轨道的声音分配到 7.1.4 的 12 个单声道输出。

## 1. 安装前确认

推荐环境：

- Ableton Live 12 Suite，或带 Max for Live 的 Ableton Live。
- macOS。
- 一张至少有 12 路物理输出的声卡。
- Ableton Live 的 Audio Output Config 里已经启用 1/2 到 11/12。

如果你的声卡少于 12 路输出，插件可以打开，但无法完整测试 7.1.4。

## 2. 解压和拷贝位置

解压后会得到这个文件夹：

```text
LR_714_Panner_v1_3_1_Public_Beta
```

推荐把整个文件夹放到 Ableton User Library 的 Max Audio Effect 目录：

```text
~/Music/Ableton/User Library/Presets/Audio Effects/Max Audio Effect/LR_714_Panner_v1_3_1_Public_Beta/
```

如果你的 User Library 不在默认位置，请在 Ableton Live 里打开：

```text
Settings / Preferences > Library > Location of User Library
```

然后进入这个 User Library，放到：

```text
Presets/Audio Effects/Max Audio Effect/
```

重要：不要只拷贝 `LR_714_Panner_v1_3_1.amxd`。这个插件需要同文件夹里的 `.js` 和 `.maxpat` 依赖文件，整个文件夹必须保持在一起。

## 3. 包内文件说明

必须保留：

```text
LR_714_Panner_v1_3_1.amxd
BrowseRoutingInline_avenir.maxpat
RoutingObjects.maxpat
lr_714_gains_comfy.js
lr_714_pad_avenir_bigger.js
lr_714_meter_avenir.js
lr_714_testfreq.js
lr_logo.js
README_FIRST.txt
版本说明_v1_3_1.txt
使用说明_LR_714_Panner_v1_3_1.md
```

其中 `LR_714_Panner_v1_3_1.amxd` 是要拖进 Live 的插件本体，其余文件是界面、路由和算法依赖。

## 4. 在 Ableton Live 里加载插件

方法 1：从 Live Browser 加载。

```text
User Library > Presets > Audio Effects > Max Audio Effect > LR_714_Panner_v1_3_1_Public_Beta
```

把 `LR_714_Panner_v1_3_1.amxd` 拖到一条 Audio Track 上。

方法 2：从 Finder 直接拖入。

把 `LR_714_Panner_v1_3_1.amxd` 从 Finder 拖到 Ableton Live 的 Audio Track 设备区域。

插件应该放在发声轨道上，也就是你要做 7.1.4 panning 的那条音频轨道。不要把它放在 Return Track 或 Master Track 上做第一次测试。

## 5. 轨道必须设置成 Sends Only

加载插件后，这条轨道的输出必须这样设置：

```text
Audio To = Sends Only
```

有的界面会把这个概念叫做 Send Only，但 Ableton Live 英文界面通常显示为 `Sends Only`。

原因：插件自己通过内部 12 路 `plugout~` 直接输出到声卡通道；如果轨道还走 `Main`，你会同时听到 Main 输出和插件直出的声音，结果会变成重复输出、声像错误或电平判断错误。

正确状态：

```text
Audio Track
Audio To: Sends Only
Monitor: Auto 或 In，按你的音源需求选择
```

## 6. Live 声卡输出设置

在 Ableton Live 打开：

```text
Settings / Preferences > Audio > Output Config
```

至少启用这些输出对：

```text
1/2
3/4
5/6
7/8
9/10
11/12
```

如果你的声卡输出名字带设备名，例如 `15/16 BBL VCA`、`17/18 Manley`，Live 菜单里会显示你的声卡名字，这是正常的。

## 7. ROUTING 区域设置

插件右侧 `ROUTING` 区有 3 列：

```text
PAIR | TYPE | CH
```

含义：

- `PAIR`：插件内部的输出对。
- `TYPE`：输出类型，正常使用选择 `Ext. Out`。
- `CH`：声卡输出通道对。

标准 12 路输出设置：

```text
PAIR 1/2   TYPE Ext. Out   CH 1/2
PAIR 3/4   TYPE Ext. Out   CH 3/4
PAIR 5/6   TYPE Ext. Out   CH 5/6
PAIR 7/8   TYPE Ext. Out   CH 7/8
PAIR 9/10  TYPE Ext. Out   CH 9/10
PAIR 11/12 TYPE Ext. Out   CH 11/12
```

Live 的外部输出菜单按 stereo pair 显示，所以这里是 6 个 stereo pair；插件内部实际输出是 12 个 mono channel。

## 8. 7.1.4 通道顺序

插件内部固定通道顺序：

```text
1  L
2  R
3  C
4  LFE
5  Ls
6  Rs
7  Lrs
8  Rrs
9  Ltf
10 Rtf
11 Ltr
12 Rtr
```

对应到输出对：

```text
1/2   = L / R
3/4   = C / LFE
5/6   = Ls / Rs
7/8   = Lrs / Rrs
9/10  = Ltf / Rtf
11/12 = Ltr / Rtr
```

如果你的实际音箱接线顺序不同，请在 ROUTING 区把 CH 改到你的声卡实际输出对。

## 9. 左侧 TEST 区

TEST 区用于检查声卡通道和插件输出。

### TEST

测试信号开关。

- 关：不产生测试信号。
- 开：插件内部产生 sine test tone。

第一次检查通道时，可以先不开音乐，只打开 TEST。

### VOL

测试信号音量。

范围：

```text
0 = -inf dB
100 = 0 dB
```

建议第一次测试从低电平开始，确认声卡通道和音箱连接正常后再提高。

### HZ

测试信号频率。

控制范围：

```text
20 Hz 到 20000 Hz
```

旋钮中点：

```text
1000 Hz
```

推荐初始测试频率：

```text
1000 Hz
```

## 10. XY / Z 声像窗口

中间的窗口显示 7.1.4 声场位置。

显示标签：

```text
L / R / C / LFE
Ls / Rs
Lrs / Rrs
Ltf / Rtf
Ltr / Rtr
```

黄色球代表当前声像中心。

操作：

- 在 XY 窗口里拖动黄色球，可以改变 X / Y 位置。
- Z 高度通过 `Z` 旋钮控制。
- X / Y / Z 旋钮变化时，XY 窗口会同步显示。

坐标含义：

```text
X = 左右位置，-1.00 是左，0.00 是中间，1.00 是右
Y = 前后位置，1.00 是前，0.00 是中间，-1.00 是后
Z = 高度位置，0.00 是底层，1.00 是上方高度层
```

## 11. SHAPE / SPACE 控制区

这一版保留 6 个核心控制：

```text
Spread / Focus / LFE
X / Y / Z
```

这些是推荐用于自动化和 MIDI mapping 的主要控制。

### Spread

控制声像扩散范围。

范围：

```text
0 到 100
```

数值越高，声音会更宽地分配到周围扬声器；数值越低，声音更接近当前中心位置。

### Focus

控制声像聚焦程度。

范围：

```text
0 到 100
```

数值越高，能量越集中，XY 窗口里的黄色范围圈会更小；数值越低，能量更松散，黄色范围圈会更大。

### LFE

控制 LFE 通道发送量。

范围：

```text
0.00 到 1.00
```

注意：LFE 是独立发送量，不是完整的低频分频器。实际演出时建议从 0 开始慢慢加，避免 LFE 通道突然过大。

### X

用于 MIDI mapping / automation 的左右位置控制。

范围：

```text
-1.00 到 1.00
```

### Y

用于 MIDI mapping / automation 的前后位置控制。

范围：

```text
-1.00 到 1.00
```

### Z

用于 MIDI mapping / automation 的高度位置控制。

范围：

```text
0.00 到 1.00
```

## 12. 电平表区域

电平表显示 12 个输出通道：

```text
L R C LFE Ls Rs Lrs Rrs Ltf Rtf Ltr Rtr
```

绿色显示当前电平，黄色线显示底部参考/峰值视觉状态。

注意：这个表显示的是插件内部送到输出前的电平，不等于声卡硬件或音箱上的最终声压。

## 13. 自动化和 MIDI Mapping

推荐自动化 / MIDI mapping 的控制：

```text
Spread
Focus
LFE
X
Y
Z
```

Ableton MIDI mapping 方法：

1. 按 `Cmd + M` 进入 MIDI Map Mode。
2. 点击插件里的目标旋钮，例如 `X`。
3. 转动你的 MIDI 控制器旋钮或推子。
4. 再按 `Cmd + M` 退出 MIDI Map Mode。

如果你要录制自动化，建议直接录 `X / Y / Z` 三个旋钮，而不是只拖 XY 窗口。

## 14. 第一次完整测试流程

按这个顺序测试：

1. 解压整个 `LR_714_Panner_v1_3_1_Public_Beta` 文件夹。
2. 把整个文件夹放进 Ableton User Library 的 Max Audio Effect 目录。
3. 打开 Live，创建一条 Audio Track。
4. 把 `LR_714_Panner_v1_3_1.amxd` 拖到这条 Audio Track 上。
5. 把这条轨道的 `Audio To` 设置成 `Sends Only`。
6. 打开 Live 的 `Output Config`，确认 1/2 到 11/12 已启用。
7. 在插件 ROUTING 区把 1/2 到 11/12 都设置成 `Ext. Out` 对应通道。
8. 打开 TEST。
9. 把 VOL 慢慢提高。
10. HZ 先放在 1000 Hz。
11. 移动 X / Y / Z，观察 12 路电平表。
12. 确认声卡每个物理输出和音箱顺序正确。

## 15. 常见问题

### 插件打开后一片空白

通常是依赖文件没有和 `.amxd` 放在一起。重新解压，保留整个文件夹，再从这个文件夹里的 `.amxd` 打开。

### TEST 没声音

按顺序检查：

```text
TEST 是否打开
VOL 是否大于 0
Audio To 是否为 Sends Only
ROUTING 是否选择 Ext. Out
CH 是否选择了真实声卡输出
Live Output Config 是否启用了对应输出
声卡物理输出是否接到音箱
轨道是否被 mute
```

### 有表但音箱没声音

插件内部已经有信号，问题通常在 ROUTING、Live Output Config、声卡输出或音箱接线。

### 只能看到 1/2、3/4 这种成对输出

这是 Live 的输出菜单显示方式。Live 按 stereo pair 管理外部输出，但插件内部仍然是 12 个 mono channel。

### LFE 看起来太大

先确认你用的是 v1.3.1，然后把 LFE 旋钮降到 0，再慢慢提高。LFE 通道是第 4 路，对应 `3/4` 输出对里的右侧通道。

### 声音同时从 Main 和环绕输出出来

把轨道的 `Audio To` 改成 `Sends Only`。

### ROUTING 里显示 No Output

先在 `TYPE` 选择 `Ext. Out`，再在 `CH` 选择具体声卡输出对。

## 16. 公测反馈建议

反馈时请尽量包含：

```text
Ableton Live 版本
macOS 版本
声卡型号
声卡输出数量
Live Output Config 截图
插件 ROUTING 截图
问题发生时的具体操作
是否 TEST 有声
是否电平表有反应
```

这样可以快速判断问题发生在插件、Live 路由、声卡设置还是物理接线。
