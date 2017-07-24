# Cron

## [Problem] Scripts Placed Under Cron Folders Don't Work

### Description

If you place some scripts under /etc/cron.hourly or /etc/cron.daily and other Cron folders. You may notice that they do not work with you, or an error message like this appears:

    run-parts: failed to exec /etc/cron.daily/script: Exec format error
    run-parts: /etc/cron.daily/script exited with return code 1
    
This means that you didn't specify the shell to use in the beginning of the script.

### Solution

Just insert **#!/bin/bash** or **#!/bin/sh** at the beginning of your scripts. Like:

    #!/bin/bash
    echo "Some text here"
    apt update
    ...
