[About Containers](https://github.com/IOxCyber/CyberWeb-Concepts/blob/main/Docker101/Docker-Theory.md#2-docker-containers-running-instance-of-a-docker-image)

## Container Security:
- Process of implementing the security tools and policies to protect the infrastructure (where the docker engine running, storage), software supply chain, runtime & everything in between.(eg CICD build pipeline, registery)


## Security Challenges:
It's different from traditional security `due to Complexity & Dynamism of the container environment.` like ephemeral (short lived) & stateless by design.

eg. Containers get terminated, created very frequently by Orchestrated tools.

## Container Attack Vectors:
- `Vulnerability and Misconfiguration` in each layers from Containers to Physical level.

```
Containers....Images
       ↕️
Orchestration Engine
       ↕️
Container Engine 
       ↕️
Host/Virtual Machine
       ↕️
Physical Infrastructure
```

- Vulnerabilities eg. Container escape, running containers using privileged user account.

> Key Points: Patching and vulnerability remediation must be done on images not on containers.






