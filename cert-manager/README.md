### 安装方法

``` bash
./install
```

### 使用方法

1. 创建全局签发机构 (ClusterIssuer):

   ``` bash
   kubectl apply -f issuer.yaml
   ```

   **注**:  可以修改下 issuer.yaml 中的 email 地址为自己的邮箱地址，证书快过期的时候会有邮件通知（收到通知可以不用管，cert-manager 可以自动为我们续期)

2. 创建证书 (Certificate)

   修改 `cert.yaml` 中关键信息：

   - metadata.name: Certificate 资源名称 (不重要)
   - metadata.namespace: 生成证书所在 namespace
   - spec.secretName: 生成证书的 Secret 名称 
   - spec.dnsNames: 生成的证书中包含的域名
   - spec.acme.config.domains: 生成的证书中包含的域名
   - spec.acme.config.http01.ingressClass: IngressController 配置的 ingressClass

   创建:

   ``` bash
   kubectl apply -f cert.yaml
   ```

   ​