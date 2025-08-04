# fail2ban

```bash
sudo apt install rsyslog fail2ban
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo vim /etc/fail2ban/jail.local
```

```diff
--- jail.conf   2022-11-09 23:46:15.000000000 +0800
+++ jail.local  2025-07-14 11:14:57.161447157 +0800
@@ -277,7 +277,8 @@
 # normal (default), ddos, extra or aggressive (combines all).
 # See "tests/files/logs/sshd" or "filter.d/sshd.conf" for usage example and details.
 #mode   = normal
-port    = ssh
+enabled = true
+port    = 36000
 logpath = %(sshd_log)s
 backend = %(sshd_backend)s
```

```bash
sudo fail2ban-client reload
sudo fail2ban-client status
```
