Following steps I will follow to resolve the issue.

1) Check disk usage of file system
  o df -h
2) Check disk usage of NGINX logs
  o du -sh /var/log/nginx

Possible root causes, impact and solutions.
1) Nginx access logs growing too much
  o Impact: NGINX may fail to write logs
  o Solution: clear the logs in this directory → /var/log/nginx/access.log

2) Ubuntu system logs become a lot
  o Impact: System performance degradation
  o Solution: clear the logs in this directory → /var/log/syslog

3) Temporary Files
  o Impact: System performance degradation
  o Solution: clear temp files in this directory → /tmp
