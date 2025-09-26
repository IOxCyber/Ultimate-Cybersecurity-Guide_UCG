## Container Security:
Process of implementing the security tools and policies to protect the infrastructure(where the docker engine running, storage), software supply chain, runtime & everything in between.(eg CICD build pipeline).

## Security Challenges:
It's different from traditional security `due to Complexity & Dynamism of the container environment.` like ephemeral (short lived), stateless by design.

eg. Containers get terminated, created very frequently by Orchestrated tools.

## Container Attack Vectors:

- Vulnerability and Misconfiguration in each layers from Containers to Physical level.

Containers....Images
       ↕️
Orchestration Engine
       ↕️
Container Engine 
       ↕️
Host/Virtual Machine
       ↕️
Physical Infrastructure

- Few Vulnerabilities eg. Container escape.

## Container Lifecycle Concerns:

1. Build (Image): 
Software Composition (libraries & pkgs), Vulnerabilities & misconfigurations, integrate with CICD pipeline for vulnerabilities visibility to dev teams.

2. Ship (Registry): 
Registry Scanning & Hygiene (del old & stale images), Image Source (if it's from trusted source), Vuln & MisConfig.

3. Run (Instance Infrastructure): 
Host Protection, Container Engine benchmarking, Container Orchestray benchmarking, Runtime Visibility & protection.

## Key Points:
- Patching and vulnerability remediation must be done on images not on containers.