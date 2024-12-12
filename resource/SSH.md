## Reverse tunnels

*This was how to avoid figuring what console/terminal values were needed
between the QEMU host and RHEL guest boot options to make everything pretty.*

Reverse tunneling from `host_a` to `host_b` so that `user_b` can get to
`host_a` as `user_a`, run as `user_a` on `host_a`: 
```
ssh -R 9000:localhost:22 user_b@host_b
```

..then logged in as `user_b` on `host_b`, trying to get to the `local_host`:
```
ssh -p 9000 user_a@localhost
```

See:

* `-fN` options: `ssh -fN -R 9000:localhost:22 user_b@host_b`
* `GatewayPorts` option in the remote (`host_b`) server's `sshd_config`
* `clientspecified` option in the remote (`host_b`) server's `sshd_config`
