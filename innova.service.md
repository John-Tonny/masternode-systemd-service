
# Service file

Location: /lib/systemd/system/innovad.service

```apache
[Unit]
Description=Innova Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.innovacore/innovad.pid
ExecStart=/usr/local/bin/innovad -daemon -conf=/root/.innovacore/innova.conf -datadir=/root/.innovacore
ExecStop=/usr/local/bin/innova-cli -conf=/root/.innovacore/innova.conf -datadir=/root/.innovacore stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=innovad.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/innovad.service
```