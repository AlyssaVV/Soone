# Soone
前置准入平台（Pre-access platform），支持 Windows 二进制 Shellcode 客户端与 Linux ELF 客户端，提供 Web 管理界面、沙箱智能检测、UUID 白名单管控及长轮询任务下发等功能。

### 运行

```bash
./Soone
```

启动后控制台输出：

```
========================================
   后台登录账号: admin
   后台随机密码: <随机13位>
   管理后台地址: http://0.0.0.0:58888/login
========================================

管理后台启动成功！运行在 http://0.0.0.0:58888
C2服务器(统一)启动成功！运行在 HTTPS://0.0.0.0:3208
```

- 每次启动生成新的随机密码（13 位字母数字）和新的 session 密钥
- 管理界面 session 有效期 3 小时
- 登录后访问 `http://<ip>:58888/login` 进入管理界面

---

### Linux 客户端文件编译依赖

生成 Linux 客户端文件时，管理界面支持选择目标架构 `amd64` 或 `arm64`。若服务器上没有可用的静态 musl 工具链，接口会直接返回编译失败，并提示检查环境配置。

```bash
# 推荐至少提供 `zig` 或 `musl-gcc` 之一

# Debian / Ubuntu
apt install gcc musl-tools zig

# CentOS / RHEL / Rocky
yum install gcc zig

# Alpine
apk add gcc musl-dev zig
```

### Windows-SRDI项目推荐

https://wiki.chainreactors.red/malefic/getting-started/components/srdi/
https://github.com/onedays12/Convert2Shellcode/
