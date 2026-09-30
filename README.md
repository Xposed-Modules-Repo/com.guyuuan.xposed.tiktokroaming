<p align="center">
  <img src="design/app-icon-concept.png" width="128" alt="TikTokRoaming">
</p>

<h1 align="center">TikTokRoaming</h1>

<p align="center">
  基于 libxposed API 102 的 TikTok 区域环境模拟模块
</p>

TikTokRoaming 可以在 TikTok 进程内模拟指定国家或地区的 SIM、运营商、语言、时区等环境信息，并支持隐藏部分 Android 标准 API 暴露的 VPN 状态。

> [!IMPORTANT]
> 本模块不会修改公网 IP，也不能替代代理或 VPN。TikTok 的区域判断还可能受到账号、IP、设备信息及服务端策略影响。

## 功能

- 模拟 SIM / 网络国家代码
- 模拟 MCC / MNC
- 模拟系统语言和时区
- 内置多个常用国家和地区档案
- 可隐藏部分 VPN 状态和常见隧道接口
- 可隐藏桌面启动图标
- 配置通过 libxposed Remote Preferences 同步
- 固定作用域，仅作用于 TikTok

当前支持：

```text
com.zhiliaoapp.musically
com.ss.android.ugc.trill
```

## 使用要求

- Android 8.0 / API 26+
- 支持 libxposed API 102 的 Xposed 框架
- TikTok 国际版

## 使用方法

1. 安装 TikTokRoaming。
2. 在 Xposed 管理器中启用模块。
3. 确认作用域包含 TikTok。
4. 打开 TikTokRoaming，等待模块服务连接。
5. 开启环境模拟并选择目标国家或地区。
6. 强制停止 TikTok 后重新启动。

修改配置后，建议重新启动 TikTok 使配置完整生效。

## 从源码构建

需要 JDK 17 和 Android SDK 37。

```bash
git clone https://github.com/guyuuan/TikTokRoaming.git
cd TikTokRoaming

./gradlew :app:assembleDebug
```

Debug APK：

```text
app/build/outputs/apk/debug/app-debug.apk
```

构建 Release：

```bash
./gradlew :app:assembleRelease
```

Release 默认启用 R8、代码混淆和资源压缩。

## 常见问题

### 切换地区后没有效果

确认模块已启用、TikTok 包名位于作用域内，并强制停止后重新启动 TikTok。

TikTok 的区域判断并不只依赖本地环境，因此修改区域信息不一定会直接改变推荐内容。

### 能修改 IP 吗？

不能。

本模块只修改 TikTok 进程读取到的本地环境信息，真实公网 IP 仍由当前网络、代理或 VPN 决定。

### 隐藏 VPN 能完全绕过检测吗？

不能保证。

该功能主要针对 Android 标准网络 API 和常见隧道接口，无法覆盖 Native 层、主动探测或服务端检测。

## 免责声明

本项目仅供学习、研究和个人测试。

请遵守所在地法律法规及相关平台服务条款。使用 Xposed 模块可能导致应用异常、风控或账号限制，相关风险由使用者自行承担。

本项目与 TikTok、ByteDance 及其关联公司无关。

## License

[MIT License](LICENSE)
