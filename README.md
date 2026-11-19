# TEFManager 陈什么改版

> 基于 [eternalfuture-e38299/TEFManager](https://github.com/eternalfuture-e38299/TEFManager) 的修改版。
> 原项目采用 **GNU Affero General Public License v3.0** 授权，本改版同样以 AGPL v3.0 发布。

## 这是什么

泰拉瑞亚 PE 的模组管理器（1.4.5.8 / Android）。本改版在原版基础上增加了「合集」功能，并修复了几处加载时序问题。

## 版本

| 项 | 值 |
|---|---|
| 显示版本 | 2.1.0 |
| versionCode | 2026110100 |
| 签名 | 与原版同一证书，可直接覆盖安装 |

> 版本号固定不变，任意一版（包括原版）都能互相覆盖安装，不用卸载。

## 本改版相对原版的改动

### 1. 模组合集（模组仓库页）

- 模组仓库页新增「合集」栏，位于「下载」前面
- 一个合集 = 一个 zip，里面可以混装不同加载器的模组（LuaLoader / KernelLoader …）
- 合集包只需要放模组安装包，`Collection.json` 可选（不写就用 zip 文件名当合集名）
- 卡片折叠显示合集名 + 模组数 + 总开关，点开展开看里面每个模组，各自独立开关
- 装完默认全部关闭；开关点了立刻生效
- 可以同时装多个合集（按合集名区分，不会互相覆盖）

### 2. 资源包合集（资源包页）

- 资源包页最前面新增「合集」栏（在语言包之前）
- 合集包里可以混装语言包 / 语言补丁包 / 材质包 / 字体包 / 音频包，类型自动识别
- 交互与模组合集一致

### 3. 启动时序修复

- 启动游戏前会先结束旧的游戏进程
- 原因：内核只在游戏进程初始化时读一次配置，复用旧进程会导致新加/删除的模组、材质包、音乐包不生效（表现为「要启动两次才生效」）

### 4. 协议相关

- 新增文件均带有 AGPL v3 协议头
- APK 内打包 AGPL v3 许可证全文（`assets/LICENSE`）
- 关于页的「许可证」一行可点击查看 AGPL 全文

## 安装

1. 下载 Releases 里的 APK
2. 直接覆盖安装（与原版签名、versionCode 一致，不需要卸载）
3. 如果之前装过 versionCode 更高的测试版，可能提示无法安装，卸载一次即可

## 源码

本仓库包含完整对应源码：

- `source/` 目录：完整可编译工程（Kotlin Multiplatform + Compose）
- Releases 里附带的源码 zip 与 APK 严格对应

编译方式（与原项目一致）：

```bash
export JAVA_HOME=/path/to/jdk-21
export ANDROID_HOME=/path/to/android-sdk
./gradlew :composeApp:assembleRelease
```

## 许可证

本项目遵循 **GNU Affero General Public License v3.0**，完整文本见 [LICENSE](LICENSE)。

这意味着：

- 你可以自由使用、修改、再分发
- 再分发时必须同样以 AGPL v3 开源，并提供完整对应源码
- 通过网络提供服务时，也必须向用户提供源码

## 致谢

- 原作者：[eternalfuture-e38299](https://github.com/eternalfuture-e38299)（TEFManager / TEFKernel）
- 模组加载器：LuaLoader、KernelLoader

## 免责声明

本软件与 Terraria 官方无关，仅供学习与个人使用。使用本软件修改游戏产生的任何后果由使用者自行承担。