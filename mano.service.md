
# Service file

Location: /lib/systemd/system/manod.service

```apache
[Unit]
Description=Mano Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.mano/manod.pid
ExecStart=/usr/local/bin/manod -daemon -conf=/root/.mano/mano.conf -datadir=/root/.mano
ExecStop=/usr/local/bin/mano-cli -conf=/root/.mano/mano.conf -datadir=/root/.mano stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=manod.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/manod.service
```