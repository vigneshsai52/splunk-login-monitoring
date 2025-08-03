# 🔍 Splunk SPL Queries Used

## 1. Login Status Count
```spl
index=* sourcetype="login_sourcetype"
| stats count by Status
```

## 2. Top Users by Login Attempts
```spl
index=* sourcetype="login_sourcetype"
| stats count by User
```

## 3. Top IPs with Failed Logins
```spl
index=* sourcetype="login_sourcetype" Status=FAILED
| stats count by IP
```

## 4. Brute Force Detection (more than 5 failures)
```spl
index=* sourcetype="login_sourcetype" Status=FAILED
| stats count by IP, User
| where count > 5
```

## 5. Failed Login Timeline
```spl
index=* sourcetype="login_sourcetype" Status=FAILED
| timechart count by User
```
