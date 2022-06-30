---
layout: post
title:  "Molecule Ansible testing systemd not working in Docker for Desktop Mac M1"
tags: molecule ansible mac m1 systemd D-Bus
---

# Failed to get D-Bus connection: No such file or directory

When I was running my playbook/role tests within Molecule, using the ansible service module I was greeted by the following error: 

```
fatal: [instance]: FAILED! => {"changed": false, "cmd": "/usr/bin/systemctl", "msg": "Failed to get D-Bus connection: No such file or directory", "rc": 1, "stderr": "Failed to get D-Bus connection: No such file or directory\n", "stderr_lines": ["Failed to get D-Bus connection: No such file or directory"], "stdout": "", "stdout_lines": []}
```

Apperently since version `4.3.0` of Docker Desktop they have switched to Cgroupv2. If the version of systemd in your containers is not `249` or above you will get the error above.

The solution I found was adding the following to my settings.json file within /Users/evad/Library/Group Containers/group.com.docker/:

```
"deprecatedCgroupv1": true
```

Solutions found in:
https://github.com/docker/for-mac/issues/6073
