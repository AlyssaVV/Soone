# Soone
​	**经数月打磨，前置准入平台正式上线和大家见面。我们不研发 C2、也不搬运 C2，只为所有C2提供一个安全可靠的伙伴；我们将沙箱对抗与调试对抗融为一体，为所有 C2 提供优秀的stager，让每一款 C2 都能专注深耕 Beacon 核心研发，告别那些重复繁杂操蛋的工作。**
​	

​	**对平台不再做过多的赘述，Linux 端目前暂未进行深度技术打磨，仅完成基础接入适配。因 Windows 汇编编译的客户端免杀表现稳定，暂不提供直接编译好的PE文件，仅提供 shellcode 供使用。PE2shellcode我推荐文末当中的两个项目，当然有自己转换项目只要是反射的都可以。**
​	

​	**从最初 Python 简易服务端搭建，到 Python 重构实现架构结构化，再到Go 语言全栈重构，现已实现多平台适配，整体兼容性表现优异。客户端兼容覆盖 Windows 7、WinServer 至 Windows 11 全系列系统。历经团队大量实测迭代、持续优化与修复，最终打磨出当前稳定可用版本。因团队人力有限，暂无法做到尽善尽美，若存在不足与疏漏之处，还望各位多多包涵。欢迎大家积极反馈问题与建议，我们将持续迭代优化、完善升级。觉得还行的老板点个star**
​	

​	**前置准入平台（Pre-access platform），支持 Windows 二进制 Shellcode 客户端与 Linux ELF 客户端，提供 Web 管理界面、沙箱智能检测、UUID 白名单管控及长轮询任务下发等功能**。

### 使用

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

 

### 视频演示

https://www.bilibili.com/video/BV1tHAAz2Ee9/


### **免责声明**

​	本项目仅用于网络安全技术的学习研究，若使用者在使用本项目的过程中存在任何违法行为或造成任何不良影响，由使用者自行承担全部法律责任，与项目作者无关。 
​	开发者及发布者不对因使用本工具造成的任何直接或间接损失、数据泄露、业务中断、法律纠纷或其他后果承担责任。请勿将本项目用于任何商业用途，仅供学习交流。 
​	本人不参加各类攻防演练以及境内外渗透项目，如溯源到本人id或者项目，纯属巧合。
​	使用本工具即表示您已阅读、理解并同意承担全部风险与责任。

**年年岁岁花相似 岁岁年年人不同**

### **致谢&参考**

https://wiki.chainreactors.red/malefic/getting-started/components/srdi/
https://github.com/onedays12/Convert2Shellcode/
https://github.com/fdx-xdf
https://github.com/badboycxcc
