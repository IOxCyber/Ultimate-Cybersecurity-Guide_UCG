---

# 🧠 What Snyk Looks For — Language by Language

| Language / Ecosystem | Manifest / Lock Files (Scanned by Snyk) | Notes |
|------------------------|------------------------------------------|--------|
| **JavaScript / Node.js** | `package.json`, `package-lock.json`, `yarn.lock`, `pnpm-lock.yaml` | Snyk checks npm, Yarn, PNPM dependencies & transitive packages. |
| **Python** | `requirements.txt`, `Pipfile`, `Pipfile.lock`, `poetry.lock`, `setup.py` | Covers both pip and Poetry environments. |
| **Java / Maven / Gradle** | `pom.xml`, `.gradle`, `build.gradle`, `build.gradle.kts` | Parses dependencies from Maven Central & Gradle builds. |
| **.NET / C#** | `.csproj`, `.vbproj`, `packages.config`, `project.assets.json` | Works with NuGet dependencies. |
| **Go (Golang)** | `go.mod`, `go.sum` | Checks Go modules and their indirect dependencies. |
| **Ruby** | `Gemfile`, `Gemfile.lock` | Analyzes RubyGems ecosystem. |
| **PHP** | `composer.json`, `composer.lock` | Scans Composer dependencies. |
| **Docker** | `Dockerfile` | Scans base image for OS-level CVEs. |
| **Kubernetes / Helm** | `deployment.yaml`, Helm Charts | Scans referenced images and configurations. |
| **Terraform / IaC** | `.tf` files | Looks for insecure IaC patterns and misconfigurations. |
| **C / C++** | `conanfile.txt`, `conanfile.py`, `vcpkg.json` | Checks dependencies via Conan or vcpkg. |
| **Swift / iOS** | `Podfile`, `Podfile.lock`, `Cartfile`, `Cartfile.resolved` | Scans CocoaPods and Carthage dependencies. |
| **Rust** | `Cargo.toml`, `Cargo.lock` | Uses crates.io advisory database. |
| **Scala / Kotlin** | `build.sbt`, `build.gradle.kts` | Similar to Java dependency analysis. |

---

## ⚙️ How It Works

1. **Reads Manifest Files:**  
   Builds a dependency tree from your project files.

2. **Compares with Snyk DB:**  
   Matches dependency versions against continuously updated vulnerability databases (CVE, NVD, GitHub advisories).

3. **Reports:**  
   - Vulnerable package name & version  
   - Severity (Low → Critical)  
   - Fixed version suggestion  
   - CVE ID and reference links  

---

## 🔍 Extras — Beyond Manifest Files

| Type | Example | Snyk Scan Behavior |
|------|----------|--------------------|
| **Binary Scanning** | Compiled `.jar`, `.war`, `.apk` | Snyk extracts dependency data via:<br>`snyk test --file=app.jar --scan-all-unmanaged` |
| **Container Scanning** | Docker images | Detects vulnerable OS packages (e.g., Ubuntu libs inside images). |
| **IaC Scanning** | Terraform, Kubernetes YAML | Finds misconfigurations like open ports, weak IAM roles, public buckets. |


## ⚡ Pro Tip

If your project has multiple components (code + Dockerfile + IaC), scan everything at once:

```
snyk test --all-projects

This scans:

requirements.txt → App dependencies

Dockerfile → Base image vulnerabilities

.tf / .yaml → Infrastructure configurations
```


## Quick Reference::

| Type                    | What File Snyk Needs                          |
|--------------------------|----------------------------------------------|
| App-level Dependencies   | requirements.txt, package.json, pom.xml, etc. |
| OS-level Dependencies    | Dockerfile                                   |
| Infrastructure-as-Code   | .tf, .yaml                                   |
| Binary (optional)        | .jar, .exe, .apk                             |