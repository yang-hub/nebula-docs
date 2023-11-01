# NebulaGraph Explorer release notes

## v3.6.0 (2023.10)

- Features
  - Supported [CAS](../../nebula-explorer/deploy-connect/ex-ug-deploy.md) for login authentication.
  - The iframe supported three message types: `ExplorerLogin` (instead of `NebulaGraphExploreLogin`), `ExplorerAddCanvasElements` and `ExplorerClearCanvas`.
- Enhancements
  - Compatibility
    - Since the database table structure has changed, you need to set `DB.AutoMigrate` to `true` in the configuration file, and the system will automatically upgrade and adapt the existing historical data.

      If the tables were created manually after you consulted our after-sales staff, please modify these tables manually: `task_infos`, `task_effects`, `sketches`, `schema_snapshots`, `favorites`, `files`, `datasources`, `snapshots`, `templates`, `icon_groups`, and `icon_items`.

      For example:

      ```mysql
      ALTER TABLE `task_infos` ADD COLUMN `b_id` CHAR(32) NOT NULL DEFAULT '';
      UPDATE TABLE `task_infos` SET `b_id` = `id`;
      CREATE UNIQUE INDEX `idx_task_infos_id` ON `task_infos`(`b_id`);

      ALTER TABLE `task_effects` ADD COLUMN `b_id` CHAR(32) NOT NULL DEFAULT '';
      UPDATE TABLE `task_effects` SET `b_id` = `id`;
      CREATE UNIQUE INDEX `idx_task_effects_id` ON `task_effects`(`b_id`);
      ...
      ```

  - High availability
    - Supported [high availability architecture](../../nebula-explorer/faq.md).

  - Usability
    - Supported changing database user's password or whitelist individually. However, due to nGQL syntax compatibility issues, the IP whitelist modification function is disabled when connecting to graph databases 3.5.x and below. You can modify the IP whitelist by executing the nGQL statement for the corresponding database version.

- Deprecated
  - Deprecated `OAuth.xxx` configuration in the configuration file, please use `SSO.xxx` instead. However, backward compatibility is maintained in 3.x versions.
  - Deprecated `SqliteDbFilePath` configuration in the configuration file, please use `DB.SqliteDbFilePath` instead.
  - Deprecated `TaskIdPath` configuration in the configuration file.
  - Deprecated `NebulaGraphExploreLogin` message type in iframe, please use `ExplorerLogin` instead. However, backward compatibility is maintained in 3.x versions.
