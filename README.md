# Brute-force-log-detector
Detects brute-force login attempts by reading a server log for suspicious IPs with repeated failed (401) requests, written in Python.

## How it works
Each server log line is checked with a regular expression to extract the 
client IP, the requested route, and the HTTP status code. Requests 
that return `401 Unauthorized` are counted for each IP address. Any IP address
with 3 or more failed attempts is flagged as a probable brute-force 
attempt.

## How to use
Place your log file as `server.log` in the same directory and run:

    python brute_force_detector.py

Outputs each flagged IP and its number of failed attempts.

## Example log line
    203.0.113.42 - - [12/Aug/2026:10:15:32] "POST /login HTTP/1.1" 401
