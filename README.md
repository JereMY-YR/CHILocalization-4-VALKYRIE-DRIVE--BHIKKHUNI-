# CHILocalization-4-VALKYRIE-DRIVE--BHIKKHUNI-
女武神驱动 -比丘尼- 中文化方案

> 非官方简体中文汉化补丁，仅用于技术交流，请支持正版。

## 项目简介

本项目为 PS Vita 游戏 **《VALKYRIE DRIVE -BHIKKHUNI-》** 的简体中文汉化。

| 项目 | 信息 |
| --- | --- |
| 游戏名称 | VALKYRIE DRIVE -BHIKKHUNI- |
| 中文名 | 女武神驱动：比丘尼 |
| 游戏编号 | PCSG00632 |
| 日版版本 | 1.07 / 官方最新升级补丁 |
| 当前汉化版本 | **0.9** |
| 发布格式 | xdelta |

本补丁不包含完整游戏本体、官方升级补丁或 DLC 安装包。

## 汉化范围

- 主线与角色剧情文本
- 系统菜单、教程、提示和固定 UI 文本
- 交流室评论与 Boss / 战斗字幕
- 字体资源
- UI 贴图资源
- 商店、服装、饰品、教程、舞台与敌人资料


## 兼容性

- 仅支持日版 **PCSG00632 1.07**
- PS Vita 需安装可用的 **rePatch** 插件
- 不支持港版、美版或其他游戏编号
- 未在其他版本上测试
- Vita3K 模拟器未测试
- 某补丁未测试
- 存在某处恶行bug触发即崩溃，因后来多次测试没有再复现过

使用错误的游戏版本、错误的基础文件或不完整的 DLC 都可能导致补丁校验失败、黑屏或加载卡死。

## 下载

请前往本仓库的 **Releases** 页面下载。

推荐使用 xdelta 版本：

```text
VALKYRIE_DRIVE_BHIKKHUNI_CN_0.9_20261031_xdelta.zip
```


### SHA256

```text
872688160B98CC238C772301DFB3C18D298A20C01F43A292BC0A12EDE5CE28F7  VALKYRIE_DRIVE_BHIKKHUNI_CN_0.9_20261031_xdelta.zip
```

## 安装完整 rePatch 包

1. 安装日版游戏本体。
2. 将游戏升级至官方 **1.07** 补丁。
3. PS Vita 安装 rePatch 插件。
4. 解压完整包。
5. 将自行合成后的 `rePatch` 文件夹复制到 PS Vita 根目录：

```text
ux0:
└─ rePatch
   └─ PCSG00632
      └─ Resource
```

最终路径应类似：

```text
ux0:rePatch/PCSG00632/Resource/Database/
ux0:rePatch/PCSG00632/Resource/Font/
ux0:rePatch/PCSG00632/Resource/UI/
```

复制完成后重新启动游戏。

## 使用 xdelta 补丁

本仓库发布的 xdelta 压缩包**不附带 `xdelta3.exe`**。
请自行获取 xdelta 

### 一、准备原版文件

自行合法获取解密后的所有所需文件。
确保游戏本体和官方 1.07 升级补丁均已正确安装。

### 二、应用补丁

在 xdelta 包目录执行：

```powershell
.\apply_xdelta.ps1 `
  -AppRoot "D:\PCSG00632\app\PCSG00632" `
  -PatchRoot "D:\PCSG00632\patch\PCSG00632" `
  -OutRoot "D:\PCSG00632\output" `
  -Xdelta3 "D:\tools\xdelta3.exe"
```

脚本会优先从 `PatchRoot` 读取官方补丁文件，缺失时再使用 `AppRoot`。

生成结果位于：

```text
output\rePatch\PCSG00632\
```

### 三、手动应用单个补丁

也可以使用 xdelta3 或 DeltaPatcher 手动应用：

```text
xdelta3 -d -f -s <原版文件> <补丁文件> <输出文件>
```

xdelta 包内共有 **90 个逐文件补丁**，每项对应路径均已记录在：

```text
xdelta_manifest.csv
```

## 已知限制

- 仅适用于日版 1.07。
- DLC 游戏文件未包含在本次 rePatch 包中，请保留自己合法安装的完整 DLC 资源。
- Vita3K 未测试，不保证 3D 演出与贴图表现。

## 故障排查

### xdelta 提示 source checksum mismatch

基础文件不是日版 1.07，或 App / Patch 目录选择错误。

请确认：

- 游戏编号为 PCSG00632；
- 已安装官方 1.07 补丁；
- 使用 `OpenDecrypted` 导出的文件；
- 没有把补丁应用到旧汉化文件上。

### 启动后仍显示日文

请确认 rePatch 插件已加载，并检查文件是否位于：

```text
ux0:rePatch/PCSG00632/
```

### 某个功能黑屏或卡加载

请记录：

- 所在场景；
- 触发角色；
- 选择支路径；
- 是否安装 DLC；
- 截图或短录像。

## 构建说明

本项目使用逐文件 xdelta 发布。生成补丁的基本命令为：

```text
xdelta3 -e -9 -s <原版文件> <汉化文件> <输出.xdelta>
```

数据库和 UI 封包保持原文件大小与结构；DXT 贴图仅重新编码发生变化的 4×4 数据块。

## 致谢

- 感谢 [jmacd/xdelta](https://github.com/jmacd/xdelta) 提供差分补丁工具；
- 感谢 rePatch 插件及其开发者；
- 感谢参与文本校对、UI 润色和实机测试的朋友；
- 感谢所有提供问题复现记录与修改建议的测试者。

## 免责声明

- 本项目为非官方汉化，仅供技术交流；
- 本项目不包含完整游戏文件；
- 补丁只能用于使用者本人合法持有的游戏及解密副本；
- 请勿用于商业用途或二次售卖；
- 请支持正版游戏。
