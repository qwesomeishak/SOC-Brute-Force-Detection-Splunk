## 🔍 View All Authentication Events

index=windows (EventCode=4624 OR EventCode=4625)

| table _time, host, user, src_ip, EventCode, status

| sort _time


## 🚫 Failed Login Attempts by IP and User

index=windows EventCode=4625

| stats count as failed_attempts by src_ip, user

| sort -failed_attempts


## ⚠️ Brute Force Detection (Failed + Success Pattern)

index=windows (EventCode=4625 OR EventCode=4624)

| bin _time span=5m

| stats count(eval(EventCode=4625)) as failed_attempts count(eval(EventCode=4624)) as success_attempts by src_ip, user, _time
        
| where failed_attempts >= 5 AND success_attempts >= 1


## 🌐 External IP Detection (Filtering Internal Traffic)

index=windows (EventCode=4625 OR EventCode=4624)

| where NOT (like(src_ip, "192.168.%") OR like(src_ip, "10.%") OR like(src_ip, "172.%"))

| table _time, user, src_ip, EventCode

| sort _time


## 👤 User Activity Timeline

index=windows (EventCode=4624 OR EventCode=4625)

| search user="john"

| table _time, src_ip, EventCode

| sort _time
