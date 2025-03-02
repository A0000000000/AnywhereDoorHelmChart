# AnywhereDoorHelmChart
* 用于部署AnywhereDoor项目下的所有容器到Kubernetes中

## 使用方式
* 将仓库clone到安装有Kubernetes集群的Master节点上
* 在Kubernetes所有节点上准备拉取好AnywhereDoor相关的镜像(最好是配置一个Registry仓库，把镜像都推送到仓库里，每个节点自己从仓库拉取所需的镜像)
* 完善anywhere-door/values.yaml文件
* 安装Helm，并在仓库的根目录执行`helm install anywhere-door ./anywhere-door`
* 执行完成后，会在用户自己配置的名称空间里创建以下资源
    * mysql容器及对应service
    * 控制平面、后台管理、后台管理WebUI对应的容器及Service
    * 飞书bot、微信bot机器人容器及对应服务(注意微信bot不会对集群外暴露端口，登录请手动部署一个NodePort类型的Service)
    * aira2、glances、pve、k8s插件容器及服务
