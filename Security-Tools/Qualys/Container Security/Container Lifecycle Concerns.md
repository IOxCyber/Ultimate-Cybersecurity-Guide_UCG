[About Containers](https://github.com/IOxCyber/CyberWeb-Concepts/blob/main/Docker101/Docker-Theory.md#2-docker-containers-running-instance-of-a-docker-image)

## Container Lifecycle Concerns:

1. Build (Image): 
Software Composition (libraries & pkgs), Vulnerabilities & misconfigurations, integrate with CICD pipeline for vulnerabilities visibility to dev teams.

2. Ship (Registry): 
Registry Scanning & Hygiene (del old & stale images), Image Source (if it's from trusted source), Vuln & MisConfig.

3. Run (Instance Infrastructure): 
Host Protection, Container Engine benchmarking, Container Orchestray benchmarking, Runtime Visibility & protection.