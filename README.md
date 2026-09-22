# Brute-force-log-detector
Detects brute-force login attempts by reading a server log for suspicious IPs with repeated failed (401) requests, written in Python.

## How it works
Each server log line is checked with a regular expression to extract the 
client IP and the HTTP status code. Requests 
that return `401 Unauthorized` are counted for each IP address. Any IP address
with 3 or more failed attempts is flagged as a probable brute-force 
attempt.

## How to use
Place your log file as `server.log` in the same directory and run:

    python brute_force_detector.py

Outputs each flagged IP and its number of failed attempts.

## Example log line
    198.51.100.23 - - [16/Aug/2026:09:14:02] "GET /index.html HTTP/1.1" 200 1024
