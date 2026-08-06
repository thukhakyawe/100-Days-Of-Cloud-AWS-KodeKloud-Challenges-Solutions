The Nautilus Development Team is preparing for a major update to their database infrastructure. To ensure a smooth transition and to safeguard data, the team has requested the DevOps team to take a snapshot of the current RDS instance and restore it to a new instance. This process is crucial for testing and validation purposes before the update is rolled out to the production environment. The snapshot will serve as a backup, and the new instance will be used to verify that the backup process works correctly and that the application can function seamlessly with the restored data.

As a member of the Nautilus DevOps Team, your task is to perform the following:

    Take a Snapshot: Take a snapshot of the devops-rds RDS instance and name it devops-snapshot (please wait devops-rds instance to be in available state).

    Restore the Snapshot: Restore the snapshot to a new RDS instance named devops-snapshot-restore.

    Configure the New RDS Instance: Ensure that the new RDS instance has a class of db.t3.micro.

    Verify the New RDS Instance: The new RDS instance must be in the Available state upon completion of the restoration process.