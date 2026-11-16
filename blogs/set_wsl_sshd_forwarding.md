# Setting up Win-to-WSL sshd Forwarding

Even though WSL has mirrored network mode, enabling barely distinguishable
ip/port usage between Win-host and WSL. However, according to my search
results, the sshd (0.0.0.0:22) port cannot be automatically mirrored.

Therefore, we need to use the portproxy cmdlet in Win-host to forward
Win's 2222 port, for example, to WSL's 22 port, along with some
toggling with the firewall. This approach has gone through tests and
proved workable.

Moreover, you may want to turn on the "AllowHostAddressLoopback" feature
for some hard-to-explain reasons.

2026.11.16

