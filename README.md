# proxy-configs

自用的代理软件分流模板及规则集

## 推荐软件

| 平台 | 推荐 |
| --- | --- |
| Linux / Windows | [mihomo 裸核](https://github.com/MetaCubeX/mihomo) |
| iOS / iPadOS | [Loon](https://nsloon.com/) |
| macOS | [Sparkle](https://github.com/xishang0128/sparkle) / [FlClash](https://github.com/chen08209/FlClash) |
| Android | [FlClash](https://github.com/chen08209/FlClash) / [ClashMetaForAndroid](https://github.com/MetaCubeX/ClashMetaForAndroid) |

## 配置

### mihomo 裸核

#### Linux

参考 [mihomo docs - Install](https://wiki.metacubex.one/startup/service/) 配置 systemd 服务。

#### Windows

1. 下载 [mihomo-windows-amd64.exe](https://github.com/MetaCubeX/mihomo/releases) 并放入工作目录；
2. 将 `mihomo/full.yaml` 复制为同目录下的 `config.yaml`，填写 `proxies` 与 `proxy-providers`；将 `mihomo/start.vbs` 复制到同目录下；
3. 打开「任务计划程序」→「创建任务」：
   - **常规**：名称 `mihomo-core`，勾选「使用最高权限运行」，配置选择 `Windows 10`；
   - **触发器**：新建，「任何用户登录时」；
   - **条件**：取消勾选「只有在计算机使用交流电源时才启动此任务」；
   - **操作**：新建，「启动程序」，选择 `start.vbs`。

### Loon

1. 导入 `Loon/standard.lsr`；
2. 流量模式切换为 `自动分流`，代理模式切换为 `TUN Only`；
3. 打开 `脚本`、`复写`、`MitM` 开关；
4. 启用 `域名` 下的 `MitM over HTTP/2`、`QUIC 回退保护`，并在 `证书管理` 安装并信任 CA 证书；
5. 添加订阅，并在 `更多` - `设置` 中开启 `始终开启`；
6. 一键更新所有外部资源，完成后重新启动 Loon。

### Sparkle / FlClash / ClashMetaForAndroid

导入 `mihomo/full.yaml` 即可。

## 参考

- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/)
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat)
- [luestr/ProxyResource](https://github.com/luestr/ProxyResource)
