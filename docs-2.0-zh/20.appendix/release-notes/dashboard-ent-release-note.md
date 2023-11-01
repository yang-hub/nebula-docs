# {{dashboard_ent.name}}更新说明

## v3.6.0（2023.10）

- 功能

  - 支持 [Zone 功能](../../nebula-dashboard-ent/3.create-import-dashboard/1.create-cluster.md)的集群。
  - 支持基于[图空间容量]配置告警规则(../../nebula-dashboard-ent/4.cluster-operator/9.notification.md)。
  - 支持管理[内核账号权限](../../nebula-dashboard-ent/4.cluster-operator/10.database-user.md)。
  - 单点登录方式支持 [CAS](../../nebula-dashboard-ent/system-settings/single-sign-on.md)。

- 增强

  - 告警级别从 3 个级别变更为 5 个级别。

  - 易用性
    - 优化历史慢查询执行计划的展示。
    - 优化集群权限管理。
    - 增加 License 临期告警。
    - 创建集群时支持修改配置参数。
    - 创建集群失败时支持重试。
    - 更新配置支持热更新部分配置。
    - 告警规则支持修改指标的单位。

  - 高可用
    - {{dashboard_ent.name}}本身支持高可用架构。
    - {{dashboard_ent.name}}支持访问高可用架构的 LM。

- 缺陷修复

  - 修复查看告警详情跳转错误的问题。
  - 修复`user`角色的账号登录后需要重新安装 LM 的问题。
  - 修复通过接口操作集群时没有权限限制的问题。
  - 修复删除集群后依赖服务进程仍然存在的问题。
  - 修复节点的 Host 为域名时执行`balance data remove`操作报错的问题。

- 弃用
  - 移除自带的内核安装包。