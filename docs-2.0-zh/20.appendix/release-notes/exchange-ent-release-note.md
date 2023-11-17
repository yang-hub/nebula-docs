# NebulaGraph Exchange 更新说明

## v3.6.0（2023.8）

- 功能

  - 为 JDBC 注册 googleDialect 以支持 [BigQuery](../../import-export/nebula-exchange/use-exchange/ex-ug-import-from-jdbc.md) 数据源。
  - 支持为 VID 添加指定字符串的前缀。
  - 支持批量删除。
  - 支持批量更新。
  - JDBC 数据源支持多表查询。
  - 移除对 Guava 的依赖。