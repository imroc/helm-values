### 安装方法

1. 一键安装到集群内部:

   ``` bash
   ./install
   ```


2. 手动添加 ingress 暴露服务到外部 (stable/weave-scope chart 包暂不支持配置 Ingress, 所以要用 Ingress 的话就只有自己手动添加):

   修改 `ingress.yaml` 中关键信息

   - spec.rules.host: weave 对外访问的域名
   - spec.rules.http.paths.backend.serviceName: weave-scope 在集群内部的 Service 名称
   - metadata.annotations.kubernetes.io/ingress.class: 使用的 IngressController 配置的 ingressClass

   创建 Ingress:

   ``` bash
   kubectl apply -f ingress.yaml
   ```

   ​