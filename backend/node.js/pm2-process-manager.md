# PM2 - Process Manager

[http://pm2.keymetrics.io/](http://pm2.keymetrics.io/)

```bash
npm install pm2 -g
```

設定檔支援 Javascript, JSON and YAML

```bash
pm2 start config.js
pm2 start process.json
pm2 start process.yml

pm2 list
pm2 ls
pm2 status

pm2 logs
pm2 monit

pm2 stop all # Stop all processes
pm2 delete all # Will remove all processes from pm2 list
pm2 flush # Empty all log files
```

