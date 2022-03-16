# PM2---Python3

curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs

sudo npm install -g pm2

kiểm tra tra : pm2 status

Cài pm2 start khi khởi động máy tính pm2 startup nó sẽ ra lệnh, copy lệnh paste vào command line

Khởi động lại sudo reboot

Kiểm tra trạng thái pm2 status

Check log pm2 logs index Delete log file to null

cd .pm2/logs
cat /dev/null >index-out.log
$ pm2 restart app_name $ pm2 reload app_name $ pm2 stop app_name $ pm2 delete app_name


# 

Chạy node bằng pm2: pm2 start index.js

Lưu trạng thái pm2 save


#

pm2 init
viet

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

pm2 start ecosystem.config.js
Restart in “production” (env_production):

pm2 restart ecosystem.config.js --env production
