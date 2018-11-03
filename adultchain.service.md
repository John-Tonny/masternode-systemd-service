
# Service file

Location: /lib/systemd/system/adultchaind.service

```apache
[Unit]
Description=AdultChain Coin Service
After=network.target

[Service]
User=root
Group=root
Type=forking
PIDFile=/root/.adultchain/adultchaind.pid
ExecStart=/usr/local/bin/adultchaind -daemon -conf=/root/.adultchain/adultchain.conf -datadir=/root/.adultchain
ExecStop=/usr/local/bin/adultchain-cli -conf=/root/.adultchain/adultchain.conf -datadir=/root/.adultchain stop
Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
Alias=adultchaind.service
```

# Enable service
```bash
systemctl enable /lib/systemd/system/adultchaind.service
```