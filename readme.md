#### In case of error Elasticsearch exited unexpectedly with exit code 78
#### Possible causes can be
- Insufficient File Descriptors (ulimit setting)
- can increase file descriptor limit using `ulimit`.
- Checking current limi `ulimit -n`.
- Increase the limit temporarily (for the current session): `ulimit -n 65536`

Because SonarQube uses an embedded Elasticsearch, make sure that your Docker host configuration complies with the Elasticsearch production mode requirements⁠ and File Descriptors configuration⁠.

For example, on Linux, you can set the recommended values for the current session by running the following commands as root on the host:

```
sysctl -w vm.max_map_count=524288
sysctl -w fs.file-max=131072
ulimit -n 131072
ulimit -u 8192
```

