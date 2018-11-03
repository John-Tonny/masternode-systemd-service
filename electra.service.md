
# Service file

Location: /lib/systemd/system/Electrad.service

```apache
[Unit]
Description=Electra Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.Electra/Electrad.pid
ExecStart=/usr/local/bin/Electrad -daemon -conf=/root/.Electra/Electra.conf -datadir=/root/.Electra
ExecStop=/usr/local/bin/Electrad -conf=/root/.Electra/Electra.conf -datadir=/root/.Electra stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=Electrad.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/Electrad.service
```