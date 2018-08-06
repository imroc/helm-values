### 与 Github 集成安装方法
1. 创建 Github OAuth App  
- 进入 Github: Settings- Developer settings-OAuth Apps-New OAuth App.  
- 填写 Application Name (随意，比如 Drone)，Authorization callback URL (https://drone.imroc.io/authorize, 替换 https://drone.imroc.io 为你自己的)，然后点击 Register application，获取到 Client ID 和 Client Secret.  
2. 修改 values.yaml 中关键配置  
- server.env.DRONE_GITHUB_CLIENT: 修改为刚刚在 Github 创建的 OAuth App 的 Client ID
- ingress.hosts: 修改为自己的域名
- server.host: 修改为自己的域名
- ingress.tls.hosts: 修改为自己的域名
- ingress.tls.secretName: 修改为自己域名的证书的 Secret 名称
- server.env.DRONE_ADMIN: 修改为自己想要的管理员名字
3. 创建 Secret  
``` bash
export GITHUB_CLIENT_SECRET=<your-github-client-secret>
kubectl create secret generic drone-server-secrets -n drone --from-literal=DRONE_GITHUB_SECRET=${GITHUB_CLIENT_SECRET}
```
4. 安装  
``` bash
./install
```
