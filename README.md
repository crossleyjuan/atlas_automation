# atlas_automation

The goal of theses scripts is to perform an automation of an environment with all the rules that have been defined within the project, for example:

- Size of the deployment
- Authentication mechanism according to the environment (example: development uses SCRAM and production x509)
- Backup policies
- Alerts

This way admins will be able to define in a single place all the policies and automate the creation of their environments using atlas.

# Usage

The starting point of this script is the "create_env" script, that can be used like this:

```
./create_env -p test -e dev -t small -x 100 -b samples/backup.conf
```

# Configuration

There are few files that allows to customize the behavior:

## T-shirt Templates

In the folder templates/azure/ there are some templates with the configuration predefined as small, medium, large


## Backup options

The backup retention policies are defined in a conf file, a sample file is provided under the sample folder like this:

```
#!/bin/bash

intervalhours=8
retentiondays=3
dailySnapshotRetentionDays=3
weeklySnapshotRetentionWeeks=0
monthlySnapshotRetentionMonths=0
```

# Alerts

The folder templates/alerts/prod contains the alerts for this environment, if you require to set specific alerts dev you can create files in
the templates/alerts/dev folder and the scripts will use this whenever you create a new dev environment


