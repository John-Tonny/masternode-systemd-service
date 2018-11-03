
# Service file

Location: /lib/systemd/system/simplicityd.service

```apache
[Unit]
Description=Simplicity Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.simplicity/simplicityd.pid
ExecStart=/usr/local/bin/simplicityd -daemon -conf=/root/.simplicity/simplicity.conf -datadir=/root/.simplicity
ExecStop=/usr/local/bin/simplicityd -conf=/root/.simplicity/simplicity.conf -datadir=/root/.simplicity stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=simplicityd.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/simplicityd.service
```