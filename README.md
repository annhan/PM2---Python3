# PM2---Python3


# install nodeJS

```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
```

# install PM2

Install: ```sudo npm install -g pm2```

Status check : ```pm2 status```

pm2 Run: ```pm2 start index.js```

Lưu trạng thái ```pm2 save```

# Cài pm2 auto start when computer restae :  

```pm2 startup``` Pm2 will show command, you need to copy and past to terminal

Reboot :sudo reboot

Check log pm2 logs index Delete log file to null

```
cd .pm2/logs
cat /dev/null >index-out.log
$ pm2 restart app_name
$ pm2 reload app_name 
$ pm2 stop app_name

$ pm2 delete app_name
```

# Init PM2 python3

 - Khởi tạo ```pm2 init``` sau đó write vào ecosystem.config.js

```
module.exports = {
  apps : [{
    name: 'echo-python-3',
    cmd: 'main.py',
    interpreter: 'python3',
    //args: 'arg1 arg2',
    autorestart: false,
    watch: true,
    //pid: '/path/to/pid/file.pid',
    //instances: 4,
    max_memory_restart: '3G',
    env: {
      ENV: 'development'
    },
    env_production : {
      ENV: 'production'
    }
  }]
};
```

- Start ```pm2 start ecosystem.config.js```

- restart with args ```pm2 restart ecosystem.config.js --env production```
