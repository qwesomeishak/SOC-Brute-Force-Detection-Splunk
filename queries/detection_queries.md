# Detection and Investigation Queries

## 1. All Authentication Events.
index="window_project_logs" 

| table _time extracted_host user src_ip EventCode status

| sort _time

## 2. Failed Logins by IP and User
index="window_project_logs" EventCode=4625

|stats count as Failed_Attempts by src_ip user

## 3. Brute Force Detection Rule
index="window_project_logs" (EventCode=4624 OR EventCode=4625)

| bin _time span=5m

| stats count(eval(EventCode=4625)) as failures count(eval(EventCode=4624)) as successes by _time src_ip user

| where failures >= 3 AND successes >= 1

| sort _time

## 4. User Timeline Investigation
index="window_project_logs" user="john"

| table _time extracted_host src_ip EventCode status

| sort _time

## 5. Attacker IP Investigation
index="window_project_logs" src_ip="185.23.45.2"

| table _time extracted_host user EventCode status

| sort _time
