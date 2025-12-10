# Tailscale Remote Access Guide

> A simple, secure, zero-config method to access an internal server from anywhere — without public IP, port forwarding, or VPS.

This guide shows how to remotely access your internal/private server from any external network using **Tailscale**.

---

## 🚀 Features

* No public IP needed
* No port forwarding
* No VPS
* Works behind NAT & firewalls
* End-to-end encrypted
* Free for personal use
* Access via SSH, web UI, APIs, Jupyter, etc.

---

# 1. Install Tailscale on the Internal Server

Run the official installation script:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

Start Tailscale:

```bash
sudo tailscale up
```

You will receive a login URL like:

```
https://login.tailscale.com/a/xxxxxxx
```

Open it in your browser and sign in.

---

# 2. Verify Server Connection

Show Tailscale-assigned IPs:

```bash
tailscale ip
```

Example output:

```
100.120.55.34
fd7a:115c:a1e0:ab12:abcd:abcd:abcd:1234
```

Use **100.x.x.x** as the remote SSH address.

---

# 3. Install Tailscale on Your Client Device

Install Tailscale on the device you'll use for remote access:

| Device     | Download                                                         |
| ---------- | ---------------------------------------------------------------- |
| Windows    | [https://tailscale.com/download](https://tailscale.com/download) |
| macOS      | [https://tailscale.com/download](https://tailscale.com/download) |
| Linux      | Install via script                                               |
| Android    | Google Play Store                                                |
| iOS/iPadOS | Apple App Store                                                  |

Login using the **same Tailscale account** as your server.

---

# 4. SSH Into the Server (From Anywhere)

```bash
ssh <username>@100.120.55.34
```

You can now SSH into your internal server from any network — without exposing ports.

---

# 5. Enable Auto-Start (Optional)

```bash
sudo systemctl enable tailscaled
sudo systemctl restart tailscaled
```

---

# 6. Access Jupyter / Web / APIs Over Tailscale

Local service → Remote access:

| Local Service | Local URL                                      | Remote (Tailscale)                             |
| ------------- | ---------------------------------------------- | ---------------------------------------------- |
| JupyterLab    | [http://localhost:8888](http://localhost:8888) | [http://100.x.x.x:8888](http://100.x.x.x:8888) |
| TensorBoard   | [http://localhost:6006](http://localhost:6006) | [http://100.x.x.x:6006](http://100.x.x.x:6006) |
| Web API       | [http://localhost:5000](http://localhost:5000) | [http://100.x.x.x:5000](http://100.x.x.x:5000) |

No reverse proxy needed — Tailscale routes everything automatically.

---

# 7. Restrict SSH to Tailscale Only (Extra Security)

Edit `/etc/ssh/sshd_config`:

```
ListenAddress 100.120.55.34
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

---

# 8. Troubleshooting

### Tailscale command not found

Reinstall:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

### Can't access web services

Ensure the service binds to `0.0.0.0`, not only `localhost`.

---

# 9. Summary

Tailscale enables:

* Remote access
* Zero-configuration NAT traversal
* Private secure networking
* Access without public IP

Perfect for:

* Lab servers
* Home servers
* GPU training machines
* NAS / Linux servers
* Developers needing remote access

---

# License

MIT License

---

# 🎉 全格式已恢复！

现在你复制到 GitHub：

* 标题会显示
* 表格会显示
* 引用、代码块、分段都正常
* 不会再被当作一整段代码

---

如果你愿意，我可以：

✅ 加目录（Table of Contents）
✅ 增加网络拓扑图（Mermaid / PNG）
✅ 自动生成“Quick Start”版本
✅ 提供中文版 README

需要哪一种？
