### 安装方法

1. 修改 `values.yaml` 关键配置：

   - `ingress.hosts`: dashboard 访问域名
   - `ingress.tls`: 开启 https 时替换证书 `secretName` 和 `hosts`
   - `serviceAccount.name`: 管理员账号名，创建后可通过 `kubectl describe sa <serviceAccount>` 查看   token，登录 dashboard 的时候会用上

2. 一键安装:

   ``` bash
   ./install
   ```

   ​