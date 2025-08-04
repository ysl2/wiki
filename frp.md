# frp

> [!NOTE]
> [assets/frp](assets/frp)

## Deploy by self-hosted

<!--Refer to [assets/frp](assets/frp)-->

按照官网的教程来

<https://gofrp.org/zh-cn/docs/examples/ssh>

注意公网服务器上面需要开放相应的端口

sdu_net 一旦检测到有 frp 行为，会直接封禁 ip。因此如果要用的话，需要做 tls 加密。而且就算采用了加密，也不知道能不能行，因为没法测试了，我的腾讯云的 ip 已经被封了。

可以采用外部 frp 嵌套内部 autossh 的方法。对于封禁 ip 的网段，采用 autossh 先连接到其他不封禁的网段。然后把不封禁的这台机器的对应端口用 frp 映射出去。比如 yin3 在 2244 端口用 autossh 映射了 server-53 的 22 端口，然后再找个公网机器用 frp 映射 yin3 的 2244 端口。这样在外部访问 frp 端口，就直接映射到了 server-53 的 22 端口，并且 server-53 对应的网段还检测不到。

## Deploy by sakura frp

```bash
# which sfrpc
# ~/.Local/bin/my/sfrp/sfrpc
# ln -s ~/.Local/bin/my/sfrp/sfrpc ~/.Local/bin/sfrpc
sfrpc -c ~/.Local/bin/my/sfrp/sfrpc.ini --natfrp_tls
```
