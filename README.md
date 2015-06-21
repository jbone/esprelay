# esprelay

A tiny line-based TCP chat server designed to relay messages between 
low-power embedded computers with Internet connectivity (for example, an
Arduino with a ESP8266 WiFi module).

# Requirements

You need Python >= 2.7 and < 3 (although conversion to Python 3 would
be trivial).

Just run "python esprelay.py" and telnet to port 54321 to test it out.
Read the section below on the protocol so you know what to send.

# Configuration

If you want the program to listen on a different port, edit esprelay.py
and change the port number in the main() function.  You could also
change the host assignment to listen on a specific interface.

# Protocol

The protocol is super-simple: 

- Clients send lines of text terminated by '\n' or '\r\n' to the server
- The first line of text sent by the client declares its conversation ID;
  this can be any string
- Lines after the first line are echoed to other clients that declared
  the same conversation ID
- Clients can disconnect at any time
