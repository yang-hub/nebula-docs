# NebulaGraph Dashboard Enterprise Edition release notes

## v3.6.0 (2023.10)

- Features

  - Supported managing clusters that use the [zone feature](../../nebula-dashboard-ent/3.create-import-dashboard/1.create-cluster.md).
  - Supported the [graph space capacity alerts](../../nebula-dashboard-ent/4.cluster-operator/9.notification.md) in the alert rules.
  - Supported managing [kernel account privileges](../../nebula-dashboard-ent/4.cluster-operator/10.database-user.md).
  - Supported [CAS](../../nebula-dashboard-ent/system-settings/single-sign-on.md) for single sign-on.

- Enhancements

  - Alerts level changed from 3 levels to 5 levels.

  - Usability
    - Optimized the display of historical slow query execution plans.
    - Optimized cluster privilege management.
    - Added license expiration warning.
    - Supported modifying configuration parameters when creating clusters.
    - Supported retry when cluster creation fails.
    - Supported updating some configurations while the cluster is running.
    - Supported modifying the unit of the metrics in the alert rule.

  - High availability
    - Supported the high availability architecture for Dashboard itself.
    - Supported for accessing the LM of the high availability architecture.

- Bug fixes

  - Fixed the bug of incorrect redirection when loading alert details.
  - Fixed the bug that LM needs to be reinstalled after login with `user` role.
  - Fixed the bug that there is no permission restriction when operating the cluster through an interface.
  - Fixed the bug that the dependent service process still exists after a cluster is deleted.
  - Fixed the bug that the `balance data remove` operation reported an error when the host of a node is a domain name.

- Deprecated
  - Removed the bundled NebulaGraph installation package.