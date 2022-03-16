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


# RAW

```
# Fork mode
$ pm2 start app.js --name my-api # Name process

# Cluster mode
$ pm2 start app.js -i max        # Will start maximum processes with LB depending on available CPUs

# Listing

$ pm2 list               # Display all processes status
$ pm2 jlist              # Print process list in raw JSON
$ pm2 prettylist         # Print process list in beautified JSON

$ pm2 describe 0         # Display all informations about a specific process

$ pm2 monit              # Monitor all processes

# Logs

$ pm2 logs               # Display all processes logs in streaming
$ pm2 ilogs              # Advanced termcaps interface to display logs
$ pm2 flush              # Empty all log file
$ pm2 reloadLogs         # Reload all logs

# Actions

$ pm2 stop all           # Stop all processes
$ pm2 restart all        # Restart all processes

$ pm2 reload all         # Will 0s downtime reload (for NETWORKED apps)
$ pm2 gracefulReload all # Send exit message then reload (for networked apps)

$ pm2 stop 0             # Stop specific process id
$ pm2 restart 0          # Restart specific process id

$ pm2 delete 0           # Will remove process from pm2 list
$ pm2 delete all         # Will remove all processes from pm2 list

# Misc

$ pm2 reset <process>    # Reset meta data (restarted time...)
$ pm2 updatePM2          # Update in memory pm2
$ pm2 ping               # Ensure pm2 daemon has been launched
$ pm2 sendSignal SIGUSR2 my-app # Send system signal to script
$ pm2 start app.js --no-daemon
```


# Cài pm2 auto start when computer restae :  

```pm2 startup``` Pm2 will show command, you need to copy and past to terminal

Lưu trạng thái ```pm2 save``` để lưu app sử dụng PM2
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

# Run Python3 with pm2

- ```pm2 start app.py --interpreter python3```


# USING THE ECOSYSTEM FILE

 - Khởi tạo ```pm2 init``` create o ecosystem.config.js

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
