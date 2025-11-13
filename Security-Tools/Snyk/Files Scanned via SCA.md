🧠 What Snyk Looks For — Language by Language

Language / Ecosystem	Manifest / Lock Files (Scanned by Snyk)	Notes

JavaScript / Node.js	package.json, package-lock.json, yarn.lock, pnpm-lock.yaml	Snyk checks npm, Yarn, PNPM deps & transitive packages.
Python	requirements.txt, Pipfile, Pipfile.lock, poetry.lock, setup.py	Covers both pip and Poetry environments.
Java / Maven	pom.xml, .gradle, build.gradle, build.gradle.kts	Snyk parses dependencies from Maven Central, Gradle.
.NET / C#	.csproj, .vbproj, packages.config, project.assets.json	Works with NuGet dependencies.
Go (Golang)	go.mod, go.sum	Checks Go modules and their indirect deps.
Ruby	Gemfile, Gemfile.lock	Analyzes RubyGems ecosystem.
PHP	composer.json, composer.lock	Scans Composer dependencies.
Docker	Dockerfile	Scans base image for OS-level CVEs.
Kubernetes / Helm	deployment.yaml, helm charts	Scans referenced images and configurations.
Terraform / IaC	.tf files	Looks for insecure IaC patterns and misconfigurations.
C/C++	conanfile.txt, conanfile.py, vcpkg.json	Checks dependencies via Conan or vcpkg.
Swift / iOS	Podfile, Podfile.lock, Cartfile, Cartfile.resolved	Scans CocoaPods and Carthage deps.
Rust	Cargo.toml, Cargo.lock	Uses crates.io advisory DB.
Scala / Kotlin	build.sbt, build.gradle.kts	Similar to Java analysis.



---

⚙️ How It Works

1. Snyk reads your manifest files to build a dependency tree.


2. Compares each dependency version with Snyk’s vulnerability database (continuously updated with CVEs, GitHub advisories, NVD).


3. Reports:

Vulnerable package name & version

Severity (Low → Critical)

Fixed version suggestion

CVE ID and reference links





---

🔍 Extras — Beyond Manifest Files

Type	Example	Snyk Scan Behavior

Binary scanning	Compiled JAR, WAR, APK	Snyk can extract dependency data using Snyk CLI (snyk test --file=app.jar --scan-all-unmanaged).
Container scanning	Docker images	Finds vulnerable OS packages (e.g., Ubuntu libs inside image).
IaC scanning	Terraform, K8s YAML	Detects misconfigurations like open ports, weak IAM roles.



---

⚡ Pro Tip

If your project has both code + Dockerfile + IaC, Snyk can analyze all at once:

snyk test --all-projects

This scans:

requirements.txt (app deps)

Dockerfile (base image)

.tf / .yaml (infrastructure)



---

🧩 TL;DR — Remember This

Type	What File Snyk Needs

App-level dependencies	requirements.txt, package.json, pom.xml, etc.
OS-level dependencies	Dockerfile
Infra-as-Code	.tf, .yaml
Binary (optional)	.jar, .exe, .apk