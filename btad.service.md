
# Service file

Location: /lib/systemd/system/BitcoinAdultd.service

```apache
[Unit]
Description=Bitcoin Adult Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.BitcoinAdult/BitcoinAdultd.pid
ExecStart=/usr/local/bin/BitcoinAdultd -daemon -conf=/root/.BitcoinAdult/BitcoinAdult.conf -datadir=/root/.BitcoinAdult
ExecStop=/usr/local/bin/BitcoinAdult-cli -conf=/root/.BitcoinAdult/BitcoinAdult.conf -datadir=/root/.BitcoinAdult stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=BitcoinAdultd.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/BitcoinAdultd.service
```