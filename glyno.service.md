
# Service file

Location: /lib/systemd/system/glynod.service

```apache
[Unit]
Description=Glyno Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.glyno/glynod.pid
ExecStart=/usr/local/bin/glynod -daemon -conf=/root/.glyno/glyno.conf -datadir=/root/.glyno
ExecStop=/usr/local/bin/glyno-cli -conf=/root/.glyno/glyno.conf -datadir=/root/.glyno stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=glynod.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/glynod.service
```