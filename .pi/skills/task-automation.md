---
name: task-automation
description: Automate tasks using cron, scheduled jobs, batch processing, and scripting
---
# Task Automation

You can set up and manage automated tasks.

## Cron / Scheduled Tasks

For Windows (Task Scheduler):
```powershell
# Create a scheduled task
$action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "-File C:\path\to\script.ps1"
$trigger = New-ScheduledTaskTrigger -Daily -At "09:00AM"
Register-ScheduledTask -TaskName "MyDailyTask" -Action $action -Trigger $trigger
```

For WSL/Linux (cron):
```bash
# Edit crontab
crontab -e

# Format: minute hour day month weekday command
# Daily at 9 AM: 0 9 * * * /path/to/script.sh
```

## Batch Processing

When processing multiple files or repeated operations:
1. First process a single item to verify correctness
2. Then scale up using loops or parallel execution
3. Add logging to track progress and errors

## Monitoring

- Add error handling and logging to all automated tasks
- Set up notifications for failures
- Keep a task manifest documenting all automated jobs
