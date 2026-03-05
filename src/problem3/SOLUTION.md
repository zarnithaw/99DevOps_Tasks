## Problem 3: Diagnose Me Doctor

**Following steps I will follow to resolve the issue.**

1. Check disk usage of file system
   - `df -h`

2. Check disk usage of NGINX logs
   - `du -sh /var/log/nginx`

---

**Possible root causes, impact and solutions**

1. Nginx access logs growing too much  
   - **Impact:** NGINX may fail to write logs  
   - **Solution:** clear the logs in this directory → `/var/log/nginx/access.log`

2. Ubuntu system logs become a lot  
   - **Impact:** System performance degradation  
   - **Solution:** clear the logs in this directory → `/var/log/syslog`

3. Temporary Files  
   - **Impact:** System performance degradation  
   - **Solution:** clear temp files in this directory → `/tmp`
