# MySQL Backup Script

## Information

1. Download it on the server which it will be used.
```bash
wget https://raw.githubusercontent.com/antiproxies/bash-scripts/master/backups/mysqldump.sh -O mysqldump.sh
chmod +x mysqldump.sh
```
2. Add a cron for it.

```bash
crontab -e

# every 6 hours
0 */6 * * * /root/mysqldump.sh > /dev/null 2>&1

# every 12 hours
0 */12 * * * /root/mysqldump.sh > /dev/null 2>&1

# every 24 hours
@daily /root/mysqldump.sh > /dev/null 2>&1

```

3. Download the backups at least once a week. The script saves only 5 backups and after that it starts deleting the oldest copy. We use it once a day and copy the the generated dumps to an externel server and only keep 10 copies a time.