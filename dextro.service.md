
# Service file

Location: /lib/systemd/system/dextrod.service

```apache
[Unit]
Description=Dextro Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.dextro/dextrod.pid
ExecStart=/usr/local/bin/dextrod -daemon -conf=/root/.dextro/dextro.conf -datadir=/root/.dextro
ExecStop=/usr/local/bin/dextro-cli -conf=/root/.dextro/dextro.conf -datadir=/root/.dextro stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=dextrod.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/dextrod.service
```