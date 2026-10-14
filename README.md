# 📦🚀 ChatFiji DeepSeek Harness Installer

This repository hosts the ChatFiji DeepSeek Harness Installer and preserves an identified snapshot of the original DeepSeek Harness (DSH) source code developed by DeepSeek AI.

🟢 The Windows installer has successfully installed, built and launched DeepSeek Harness on a real Windows x64 computer.

🟢 The generated Windows launcher successfully reopened the application after the original backend shell was accidentally closed.

🟠 The first launch required an additional pnpm dependency reinstallation, explained below.

**📅 README updated: 14 October 2026 (Fiji Time)**  
**🧰 Latest installer: v1.0.3**  
**✅ Windows x64: Functionally tested**  
**🧪 macOS and Linux: Development and testing pending**  
**⚠️ Developer preview — Not security-audited or production-certified**

---

## 📥 1. Download the latest installer

### ✅ ChatFiji DeepSeek Harness Installer Kit v1.0.3

**📦 [Download Installer Kit v1.0.3](https://github.com/AonzOG/deepseek-harness-d743267/blob/master/installers/DeepSeek-Harness-Installer-Kit-v1.0.3.zip)**

**SHA-256:**

`8bd2f518518a7b725a5c07a7e5303b9f53ed59109eeb932300d4994f7c30b5de`

The ZIP includes:

- 🪟 Windows graphical installer — `.bat` and `.ps1`
- 🍎 macOS installer — `.command` and shared Unix script
- 🐧 Linux installer — `.sh` and shared Unix script
- ⚙️ Shared installation engine
- 🧪 Automated installer tests
- 📖 Bundled technical documentation

**Only the Windows installation and launch pathway has been verified through actual end-user operation.** The other operating-system installers are retained for future development and testing.

This package builds and runs the DeepSeek Harness Web UI from source. It is **not** a signed, precompiled Electron desktop installer.

---

## 🪟 2. Windows installation instructions

### 🧩 Before installation

You need:

- 💻 A Windows x64 computer.
- 🌐 An internet connection for source and dependency downloads.
- 🔧 Git 2.26 or newer installed and accessible.
- 💾 Sufficient disk space, memory and time for a large source build.

The installer downloads its own application-local Node.js 24 runtime and verifies the official download using SHA-256. It uses the repository-compatible pnpm version without requiring a system-wide Node.js installation.

### 🚀 Step 1 — Download and extract

Download `DeepSeek-Harness-Installer-Kit-v1.0.3.zip` and extract the complete archive into a folder.

**Keep all extracted installer files together.** Do not run an individual installer script without its supporting files.

### 🖱️ Step 2 — Open the Windows installer

Double-click:

`Install-DeepSeek-Harness-Windows.bat`

The graphical installer provides **Install, Repair and Uninstall** options.

Select **Install** for a new installation.

### 📂 Step 3 — Choose the installation directory

The default Windows installation destination is:

`C:\deepseek-harness`

Use **Browse** to choose another suitable writable folder if preferred.

### 🌍 Step 4 — Select the repository source

The installer supports three choices:

**1️⃣ Official DeepSeek Harness**

https://github.com/deepseek-ai/deepseek-harness

**2️⃣ ChatFiji-hosted preserved repository**

https://github.com/AonzOG/deepseek-harness-d743267

**3️⃣ Custom compatible repository**

Paste the public HTTPS Git URL of a compatible fork or imported DeepSeek Harness repository.

⚠️ The installer retrieves the selected repository's current HEAD at installation time and records the exact installed commit. Selecting the ChatFiji repository does not automatically pin future installations to its original upstream commit. Custom repositories should be treated as untrusted unless their content and installation scripts have been reviewed.

### ⚙️ Step 5 — Allow installation and compilation

The installer retrieves the source, prepares the local runtime, installs dependencies and builds the application.

The original project contains a large multi-package workspace, so installation can take considerable time.

✅ Wait until the installer reports successful completion.

The Windows installation was tested successfully with the preserved upstream application revision:

`d743267388641bc76f17c45ce8b4c231aed1d32c`

---

## ⚠️ 3. Important first-launch dependency prompt — `Y/n`

During the documented Windows test, selecting **Run Harness** caused pnpm to display:

~~~text
The modules directories will be removed and
reinstalled from scratch. Proceed? (Y/n)
~~~

### ❓ What does this mean?

The installer builds the application inside a temporary directory before moving it to its final installation location.

This relocation can leave pnpm dependency metadata or Windows directory links requiring reconstruction.

**That is the leading technical explanation for the observed prompt; its exact triggering condition has not been conclusively proven.**

### ✅ What happened during the successful test?

The confirmation proceeded as **Yes**, authorising pnpm to replace and reinstall its managed dependency directories.

The operation completed successfully:

~~~text
Packages: +1398
Progress: resolved 1398, reused 1394,
downloaded 0, added 1398, done
~~~

DeepSeek Harness then launched successfully.

### 🟠 What should users do?

If this exact prompt appears during the first launch of the documented Windows installation, users who choose to continue can enter **`Y`** and press **Enter**.

⚠️ This permits pnpm to remove and reconstruct its managed dependency directories. It may take additional time, and manually modified contents of those directories could be overwritten.

🛑 Users who are uncertain about their existing installation should not approve the operation without first checking their files and installation state.

🔧 This is a known first-launch reliability limitation. It should be corrected in a future installer version so ordinary launching does not require dependency reconstruction.

A successful test on one computer does not guarantee that the same procedure will succeed on every computer.

---

## 🌐 4. Launching DeepSeek Harness

After installation, the Windows launcher is located at:

`C:\deepseek-harness\Launch-DeepSeek-Harness.bat`

Double-click the launcher to start the backend.

### ⏳ The browser may not open immediately

The launcher starts `dsh web`. DeepSeek Harness must initialise the backend, start its local server and produce the access-token URL.

The local interface normally runs at:

`http://127.0.0.1:3080/`

The complete URL generated by the application may include a session access token.

🔐 **Do not publish or share token-bearing URLs or logs containing access tokens.**

✅ Allow the backend to finish starting before attempting to use the browser interface.

🖥️ **Keep the backend shell running while using DeepSeek Harness.** Closing it normally stops the local server.

🔄 If the backend shell is accidentally closed, reopen the generated launcher to start a new local server session.

**Verified behavior:** The generated Windows launcher successfully restarted DeepSeek Harness, and the application was subsequently used for sustained coding work.

---

## 🧪 5. Platform validation status

| Component | Status |
|---|---|
| 🪟 Windows x64 installation | ✅ Passed on one real computer |
| 🏗️ Windows application build | ✅ Passed |
| 📦 Windows first-launch dependency reconstruction | ✅ Completed successfully |
| 🌐 Local Web UI startup | ✅ Passed |
| 💻 Sustained coding activity | ✅ Passed |
| 🔄 Generated Windows launcher restart | ✅ Passed |
| 🧰 Repair and Uninstall | 🧪 Not comprehensively acceptance-tested |
| 🍎 macOS installer and launcher | ⏳ Not native-runtime tested |
| 🐧 Linux installer and launcher | ⏳ Not native-runtime tested |
| 🔐 Security and privacy audit | 🚨 Outstanding |
| 🏢 Production/SaaS deployment certification | 🚨 Not established |

The macOS and Linux installation scripts remain included in v1.0.3 for **future development, compatibility verification and native testing**.

⚠️ No claim is made that those operating-system installers have successfully installed or launched the application.

---

## 🏢 6. Intended use — ChatFiji and its Group of Companies

The ChatFiji installer was developed primarily for **ChatFiji and its Group of Companies**, including:

- 🧑‍💻 Internal software development and engineering.
- 🧪 Internal testing and controlled experimentation.
- 🖥️ Installation on organisation-managed computers and servers.
- ☁️ Preparation of DeepSeek Harness environments for ChatFiji's internal SaaS-related infrastructure and services.

This restricted intended deployment scope is designed to reduce uncontrolled operational exposure. It is **not evidence of cybersecurity or privacy protection**.

🚨 Deployment on an internal server does not automatically make software secure. Any externally accessible SaaS deployment requires its own security, privacy, operational and access-control assessments before production use.

### 🌍 Third-party use

Suitability for independent third-party installation, unrestricted consumer use, sensitive data processing and internet-exposed production operation **has not been established**.

Third parties must independently assess applicable permissions, compatibility, security, privacy, operational risk and legal requirements.

---

## 🔐 7. VIBE CODE ALERT! Security, cybersecurity and privacy — unaudited

🚨 Vibe Coded by GPT-6 Astra

⚠️ IMPORTANT SOFTWARE, SECURITY AND DEPLOYMENT NOTICE

🔴 No comprehensive, formally documented data-security, cybersecurity, privacy, penetration-testing or production-security audit has been completed or verified for the ChatFiji installer.

🔴 macOS and Linux installer execution has not yet been acceptance-tested on those operating systems.

🚨 Public availability does not establish the installer's suitability for third-party, consumer or internet-exposed production deployment.

### 🚨 CODE ALERT: NO COMPREHENSIVE SECURITY ASSURANCE

As of **14 October 2026**, no comprehensive, formally documented security or privacy assessment has been completed or independently verified for the ChatFiji installer.

Outstanding assessments include:

- 🔐 Data security and information-handling controls.
- 🛡️ Cybersecurity vulnerability assessment.
- 🧪 Penetration testing.
- 🕵️ Privacy and personal-data protection.
- 📦 Software supply-chain and dependency security.
- 🔑 Credentials, secrets and session-token protection.
- 🌐 Network exposure and server hardening.
- 🔄 Repair, update, backup and uninstallation safety.
- 🗃️ Data integrity, retention and recovery.
- 🏢 Internal and external production-deployment controls.

Automated tests, SHA-256 runtime verification, lockfile policy checks and successful application operation **do not amount to comprehensive cybersecurity or privacy certification**.

---

## ⚖️ 8. Copyright and licensing

### 📜 Original DeepSeek Harness — MIT License

**DeepSeek Harness © 2026 DeepSeek**, subject to the MIT License.

The upstream source code, copyright notices, MIT licence conditions and applicable third-party acknowledgements remain in effect.

📄 [Read the original MIT licence](LICENSE)

### 🔒 ChatFiji installer and launchers — Proprietary Copyright

**© 2026 ChatFiji. All rights reserved.**

The original installer scripts, launchers, installation-management code and associated materials owned by ChatFiji are designated as **proprietary ChatFiji software**.

Public availability of the repository or installer package does not itself grant permission to independently redistribute, sublicense, commercially exploit or incorporate ChatFiji-owned proprietary components into another product.

Any permissions beyond those expressly granted by ChatFiji require ChatFiji's written authorisation, subject to applicable law.

This proprietary designation applies only to material that ChatFiji owns or may separately license. It does **not** remove or restrict rights granted under the MIT License for DeepSeek Harness or under other applicable third-party licences.

---

## ⚠️ 9. “AS IS” disclaimer and limitation of responsibility

**THE CHATFIJI DEEPSEEK HARNESS INSTALLER AND ASSOCIATED LAUNCHERS ARE PROVIDED “AS IS” AND “AS AVAILABLE”, WITHOUT WARRANTIES OR GUARANTEES OF ANY KIND, TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW.**

ChatFiji makes no guarantee of uninterrupted operation, compatibility, fitness for a particular purpose, data security, cybersecurity, privacy, reliability or suitability for third-party production deployment.

**To the maximum extent permitted by applicable law, including applicable law in Fiji, ChatFiji and its associated entities disclaim liability for loss, damage, interruption, data loss, security incidents, compatibility failures or other consequences associated with use of ChatFiji's installer and launchers.**

No continuing obligation to provide maintenance, support, updates, bug fixes, security remediation or compatibility assistance to third parties is undertaken.

Nothing in this notice excludes rights, remedies or liabilities that cannot lawfully be excluded.

The original DeepSeek Harness software remains subject to the separate warranty and liability provisions of its MIT License.

---

## 📌 10. Original source preservation

This repository preserves the DeepSeek Harness upstream source identified by:

**Repository:** https://github.com/deepseek-ai/deepseek-harness

**Original commit:** `d743267388641bc76f17c45ce8b4c231aed1d32c`

**Upstream commit date:** 9 October 2026, 09:31 UTC (9:31 PM Fiji Time).

**Upstream version:** `0.2.1-alpha.2`

🔗 [View original upstream commit](https://github.com/deepseek-ai/deepseek-harness/commit/d743267388641bc76f17c45ce8b4c231aed1d32c)

Subsequent ChatFiji installer commits do not change the identity of the original imported source snapshot.

### 🗂️ Installer release policy

📦 **v1.0.3 is the current retained installer package.**

🗑️ Superseded, non-working v1.0, v1.0.1 and v1.0.2 ZIP files are removed from the current repository branch.

🧪 The latest bundled macOS and Linux installer scripts are retained for further testing and development.

Historical commits remain part of Git history; deleting old ZIPs from the current branch does not erase their earlier appearances from repository history.

---

**📅 ChatFiji installer notice updated: 14 October 2026.**

**📖 The original DeepSeek Harness README follows below, retained without modification for upstream documentation and attribution.**

---

# DeepSeek Harness

English | [中文](README.zh.md)

DeepSeek Harness (`dsh`) is an open-source agent harness developed by [DeepSeek AI](https://deepseek.com).

It is built on an **everything-is-a-plugin** architecture and powered by [Cordis](https://github.com/cordiverse/cordis), whose design is described in [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512).

Documentation: [https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## Developer preview

DeepSeek Harness is in _developer preview_ and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

Review the [safety notice](SAFETY.md) before running the project.

## Run

### Run from `npm`

Install `Node.js`, then run:

```sh
npx @deepseek-ai/dsh web
```

The command starts the Web UI at `http://127.0.0.1:3080` by default and opens it in the default browser for a local launch. An SSH launch only prints the host URL because the SSH client or editor owns the local forwarded address. Pass `--no-open` to run the server without opening a browser. See [Web UI guide](docs/user/guide/index.md).

### Run from source

To run from a repository checkout:

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` prepares the repository artifacts. `pnpm dsh web` uses those built artifacts without rebuilding.

## Community and support

- Submit feedback or bug reports through [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions).
- Add the [`dsh-plugin`](https://github.com/topics/dsh-plugin) topic to your plugin repository for discoverability.
- Join <a href="https://discord.gg/4MrtZUhpxg">DeepSeek Harness Discord community</a>.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Development

Start with the [development guide](docs/development.md) and [architecture documentation](docs/architecture.md).

`pnpm run dev:web` builds, serves, and rebuilds client bundles on source edits in one terminal, and `make help` lists the matching Make targets for Web and Desktop; the guide's application commands section owns the full table.

For agents, follow [AGENTS.md](AGENTS.md).

## Citation

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## License

[MIT](LICENSE)

Third-party dependencies and their licenses are disclosed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
