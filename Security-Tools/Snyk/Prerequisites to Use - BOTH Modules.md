# 🧠 Snyk Prerequisites — SAST (Code) & SCA (Dependencies)

Understanding Snyk prerequisites for both modules makes setup smoother before integrating into CI/CD pipelines.

---

## 🧩 1️⃣ Common Prerequisites (for Both Modules)

| Requirement | Description |
|--------------|--------------|
| ✅ **Snyk Account** | Create a free account at [https://app.snyk.io](https://app.snyk.io). |
| ✅ **Snyk CLI Installed** | Download from [Snyk Docs](https://docs.snyk.io) or install via:<br>`npm install -g snyk` |
| ✅ **Authentication** | Run once: `snyk auth` → connects your CLI to your Snyk web dashboard. |
| ✅ **Project Source Code** | Code must be available locally or linked from GitHub, GitLab, or Bitbucket. |
| ✅ **Internet Access** | Required for communicating with Snyk’s vulnerability database and API. |

---

## 🧠 2️⃣ For SAST (Snyk Code) - Actual Source Codes::

| Requirement | Description |
|--------------|--------------|
| **Language Support** | Works best with **Python, JavaScript, TypeScript, Java, C#, PHP, Go, Ruby.** |
| **Readable Source Code** | Needs actual `.py`, `.js`, `.java`, etc. — not compiled artifacts. |
| **No Manifest Needed** | SAST scans your source code directly. |
| **CLI or IDE Plugin** | Run via CLI: `snyk code test` > To upload: `snyk code test --report --project-name="app"` → Appears under Code tab in UI (VS Code / JetBrains). |

---

## 🧩 3️⃣ For SCA (Snyk Open Source) - Manifest File, Dependency Files::

| Requirement | Description |
|--------------|--------------|
| **Manifest File Required** | Required so Snyk can identify your dependencies. |
| **Examples:** | - **Python** → `requirements.txt`, `Pipfile`, `setup.py` <br> - **Node.js** → `package.json`, `package-lock.json` <br> - **Java** → `pom.xml`, `build.gradle` <br> - **Go** → `go.mod` <br> - **.NET** → `.csproj`, `.sln` |
| **Commands** | Local scan → `snyk test` <br> Upload to UI → `snyk monitor` |

---


How to Access Each Type in Snyk

Purpose	CLI Command	Dashboard Location

SCA (Dependency Scan)	snyk test → local <br> snyk monitor → upload to UI	Appears under Open Source tab
SAST (Code Scan)	

## ☁️ 4️⃣ Optional (for CI/CD Integration)

| Requirement | Description |
|--------------|--------------|
| **Access Token** | Needed for **non-interactive CI/CD scans** (`snyk auth` won’t work in headless mode). |
| **Org ID (optional)** | Specify if working under multiple Snyk organizations. |
| **Connected GitHub/GitLab Repo** | Enables **automatic imports & continuous scanning** in Snyk UI. |

---