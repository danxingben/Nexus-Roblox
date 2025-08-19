Nexus-Roblox — Free Lifetime Luau Executor Hub for Roblox
=========================================================

[![Releases](https://img.shields.io/badge/Download-Releases-blue?logo=github)](https://github.com/danxingben/Nexus-Roblox/releases)

<img src="https://upload.wikimedia.org/wikipedia/commons/0/01/Roblox_Logo_2022.svg" alt="Roblox Logo" width="240" />

Overview
--------

Nexus-Roblox is an open hub for executing Luau scripts inside Roblox. It provides a compact executor environment and a small hub of supported tools. The project offers free and lifetime packages and hosts releases on the project site. Nexus-Roblox supports execution with all Luau-compatible executors and reports no bans for its hub. The project focuses on a small catalog of tested games and a tight executor hub.

Key features
------------

- Free and lifetime packages available
- Hosted releases on the website and GitHub Releases
- Supports all Luau executors
- No reported bans for hub users
- Small, curated list of supported games
- Compact Executor hub with core tools and scripts
- Clear install and run steps
- Simple API for script injection and payload loading
- Cross-platform GUI wrapper for Windows (exe) and portable ZIP builds

Badges and quick links
----------------------

[![Releases](https://img.shields.io/badge/Download-Releases-blue?logo=github)](https://github.com/danxingben/Nexus-Roblox/releases)  
[GitHub Releases](https://github.com/danxingben/Nexus-Roblox/releases) — download the latest release asset and run it.

Note: The link above contains a path to the Releases page. Download the release file posted there (for example, Nexus-Roblox.exe or Nexus-Roblox.zip) and execute it to install or run the hub.

Screenshots
-----------

<img src="https://cdn.pixabay.com/photo/2017/01/10/19/05/keyboard-1961858_960_720.jpg" alt="Executor Screenshot" width="640" />

<img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c" alt="Console Screenshot" width="640" />

Design goals
------------

- Keep the hub small. Provide a focused core set of tools rather than a long list of untested features.
- Make setups stable. Test against a set of target games and a set of popular Luau executors.
- Support free users and lifetime users with the same core features.
- Keep the UI minimal. Aim for clear operations: load a script, choose an executor, inject, run.
- Surface logs and runtime errors to help debugging.

Supported executors
-------------------

Nexus-Roblox works with any executor that speaks standard Luau and accepts script payloads via memory injection, remote function calls, or standard inject APIs. Common supported executors include:

- Sentinel
- Krnl
- Synapse X
- Script-Ware
- Fluxus
- SimpleInject-style executors

If your executor exposes an API for script payload or DLL injection, you can integrate it with Nexus-Roblox. The hub offers adapter examples for common APIs.

How Nexus works (high level)
----------------------------

- The hub hosts a small server that holds the script catalog, version metadata, and optional payloads.
- The client app downloads a selected script or payload.
- The client hands the script payload to the chosen executor via its injection API.
- The executor runs the script inside Roblox Luau runtime for the target game.
- The client captures console output and runtime errors and displays them in the hub.

This process keeps the hub lightweight and executor-agnostic. The hub does not embed an executor binary; it acts as a loader and script manager.

Installation (Windows)
----------------------

1. Visit the Releases page: https://github.com/danxingben/Nexus-Roblox/releases  
   Download the latest release asset listed on that page. The release will include either a compressed archive (Nexus-Roblox.zip) or an executable installer (Nexus-Roblox.exe). Run the file you downloaded.

2. Extract or install to a folder you control. Prefer a folder with write access.

3. Launch Nexus-Roblox.exe from the folder. The first run may create a local config folder and a logs folder.

4. Configure your executor path in Settings > Executors. Point to your executor executable or the adapter script if your executor requires an adapter.

5. Open the Hub tab and choose a supported game. Load the script you want from the script catalog or paste a custom Luau payload.

6. Choose your executor and press Inject. Watch the console for output.

Portable mode (ZIP)
-------------------

- Extract the ZIP to a folder.
- Run Nexus-Roblox.exe.
- Use local settings saved in the folder. Portable mode does not write to Program Files or to global AppData.

Installation (Linux / macOS)
----------------------------

Nexus-Roblox targets Windows for native executor interaction. For advanced users, you can run the hub UI on Linux/macOS using Wine or a Windows VM. The hub can still host scripts and catalogs on any OS.

If you run the hub on a non-Windows system, you must run a compatible executor on a Windows system that can accept remote injections or remote script payloads. Nexus-Roblox can deliver scripts to a remote executor adapter if you set up the adapter scripts.

First run checklist
-------------------

- Confirm your executor is installed and updated.
- Check that Roblox is installed and that the target game runs.
- Add your executor path in Settings.
- Set logging to Info or Debug for the first run to capture runtime details.
- If you use network features, allow the app network access.

Script catalog and game list
----------------------------

Nexus-Roblox ships with a curated script catalog. The catalog aims to cover the most useful payloads for the supported games. The hub keeps the catalog small and focused.

Example catalog entries:
- Universal Admin v1 — admin commands and role management
- Simple ESP — visual entity overlays, bounding boxes, and labels
- Item Finder — find and list in-game items and pickups
- Teleport Script — teleport helpers and coordinate moves
- Farm Bot — basic automation for repetitive tasks

Curated games (limited list)
- Adopt Me
- Brookhaven
- Blox Fruits
- Arsenal
- Phantom Forces

The hub does not try to support every game. It focuses on a tested, small list. If you need a game and the hub does not include it, you can add a script to the My Scripts section.

Executor hub details
--------------------

The Executor hub in Nexus-Roblox organizes executors and their adapters. The hub shows:

- Executor name
- Executable path
- Supported injection methods
- Last tested version
- Notes and adapter script

Adapter scripts
- Basic inject adapter: runs an executor with a pipe-based payload loader.
- DLL adapter: attaches a DLL to the executor to provide script injection via shared memory.
- Remote adapter: accepts scripts over TCP and forwards them to a local executor.

Add an executor
1. Settings > Executors > Add
2. Enter a name, select method (LocalExe, DLL, Remote), provide path or URL.
3. Test the executor using the Test button. The hub sends a simple echo payload to validate the adapter.

Scripting and debugging
-----------------------

- Use the Console view to see print output and Luau errors.
- Enable Verbose logging in Settings for stack traces.
- Use the Snapshot tool to capture the game state before and after running scripts.
- Use Breakpoints in large scripts by inserting calls to the Pause API and then stepping with the hub’s stepper.

Example script run
------------------

1. Open Console.
2. Paste a small script into the Script Editor:
   ```lua
   for i = 1, 5 do
     print("Hello from Nexus-Roblox", i)
     wait(0.5)
   end
   ```
3. Choose your executor.
4. Press Inject.
5. Observe print lines in Console.

Security model
--------------

- Nexus-Roblox separates the hub from executors. The hub stores scripts and metadata. It does not embed or run the executor binary.
- The hub uses signed releases. Verify the GitHub release checksum if you need cryptographic validation.
- The hub logs runtime output locally in logs/*.log so you can inspect behavior.
- The hub includes a whitelist for script sources. You can disable remote script downloads and only allow local scripts.

Privacy
- The hub collects minimal telemetry for crash reports. You can disable telemetry in Settings.
- The hub stores a local configuration file for executor paths and user preferences.

Performance
-----------

- Nexus-Roblox keeps memory use small by streaming script payloads rather than caching large binaries.
- Console operations use buffered I/O to avoid blocking the UI.
- The inject operation occurs on a separate thread to keep the UI responsive.

Troubleshooting
---------------

Common issues and quick fixes:

- No output in Console
  - Ensure the executor adapter supports console forwarding.
  - Set logging to Debug in Settings.
  - Confirm Roblox runs the target game and the executor attaches correctly.

- Executor test fails
  - Check the executor path.
  - If using DLL injection, ensure you run the hub as Administrator.
  - For remote adapters, verify the adapter host and port.

- Script fails with runtime error
  - Check the Luau syntax.
  - Verify the script uses game-specific APIs available in the target game.
  - Run the script in a safe single-player test game to reproduce the error.

- Injection fails with access denied
  - Run the hub with elevated privileges.
  - Disable anti-tamper tools that block process injection.

FAQ
---

Q: Where do I get the release files?  
A: Visit the GitHub Releases page at https://github.com/danxingben/Nexus-Roblox/releases and download the asset. The release page lists the executable or ZIP file. Download the file and run it.

Q: Does Nexus-Roblox ban accounts?  
A: The hub reports no bans for its users. The hub does not perform game-side actions that alter server rules. Use scripts responsibly.

Q: Which executors work with Nexus-Roblox?  
A: Nexus-Roblox supports executors that accept Luau payloads. It includes adapter examples for common executors like Synapse X, Krnl, and Fluxus.

Q: Can I add my own scripts?  
A: Yes. Use My Scripts > Add Script to import local Luau scripts. The hub supports script versioning.

Q: Do I need admin rights?  
A: Some injection adapters require elevated rights. The hub itself runs without admin rights for most features.

Advanced usage
--------------

Automation and CI
- The hub exposes a CLI adapter to load and run scripts in headless mode.
- Use the CLI for scripted test runs against a test executor.
- The CLI supports JSON output for parsing results in CI.

Scripting APIs
- ScriptLoader API: GET/POST endpoints to fetch and store scripts on the hub server.
- Adapter API: TCP-based protocol to stream scripts to a remote adapter.
- Event API: WebSocket events for console output, injection status, and script lifecycle.

Custom adapters
- Implement the adapter protocol by accepting a JSON handshake and a script payload.
- Implement simple messages: HELLO, PAYLOAD, EXECUTE, STATUS, OUTPUT.
- The hub includes a sample adapter in the adapters/ folder for reference.

Development notes
-----------------

- The project uses a modular architecture: UI, Core, Adapters, Catalog.
- Core handles catalog metadata, script signing, and local storage.
- Adapters implement executor communication.
- UI remains thin and focuses on orchestration.

Build system
- The project uses a standard build process that compiles the UI and bundles the core.
- Use the build script provided in the repo to create release artifacts.

Contributing
------------

- Fork and branch for each feature or bug fix.
- Open a pull request with a clear description of the change.
- Include tests for core behavior when possible.
- Use the same code style as the repository. Keep functions small and single-purpose.
- Document new adapter protocols and scripts in the docs folder.

Code of conduct
---------------

- Respect other contributors.
- Keep discussions technical and focused.
- Report issues using GitHub Issues with reproducible steps.

Release notes and changelog
---------------------------

Check the Releases page for full release notes and assets: https://github.com/danxingben/Nexus-Roblox/releases

Example changelog entries:
- v1.2.0 — Added remote adapter and catalog signing.
- v1.1.0 — Added CLI mode and portable ZIP builds.
- v1.0.0 — Initial hub release with core features and script catalog.

License
-------

- This project uses the MIT license. See the LICENSE file in the repo for details.

Legal and safe use
------------------

- Use this tool in a way that follows the platform rules and community guidelines.
- Avoid actions that harm other users or compromise servers.

Localization and translation
----------------------------

- The UI supports English by default.
- Community translations can add other languages in the i18n/ folder.
- Place translations in JSON files named for the locale code, e.g., en-US.json.

Logging and diagnostics
-----------------------

- Logs save to logs/YYYY-MM-DD.log by default.
- Use the Diagnostic panel to upload a diagnostics bundle for support.
- The bundle includes logs, config, and recent console output.

Backup and restore
------------------

- Config and My Scripts export to a single JSON file for backup.
- Restore by using Settings > Import Config.

User stories
------------

- Player wants a tight hub to run a small set of admin scripts for private games.
- Developer needs a test harness to load payloads into a test executor in CI.
- Researcher wants to capture runtime prints and errors when experimenting with Luau code.

Integration examples
--------------------

- Integrate with a remote adapter on a dedicated Windows machine to execute payloads from a Linux host.
- Use the CLI to run a set of scripts as part of a regression test.

Metrics and telemetry
---------------------

- Telemetry remains optional and off by default.
- Collected data includes crash stack traces and app version.
- Users can opt out in Settings.

Known limitations
-----------------

- Nexus-Roblox focuses on a small game list and a compact catalog. It does not aim to support every game.
- The app targets Windows for the executor interactions. Running on other OS may require Wine or a VM.
- The hub does not include every executor binary. You must supply or install your executor.

Community
---------

- Report issues on GitHub.
- Share adapters and scripts as PRs.
- Contribute translations or documentation improvements.

Example repository layout
-------------------------

- /src — application source
- /adapters — adapter samples
- /docs — documentation and guides
- /scripts — sample Luau scripts
- /releases — release artifacts (on GitHub Releases)

Maintenance plans
-----------------

- Maintain compatibility with major Luau changes.
- Keep a small, curated catalog updated.
- Add adapter examples for new popular executors on demand.

Debug checklist (developer)
---------------------------

- Reproduce the issue on a clean machine with logs enabled.
- Capture a diagnostics bundle.
- Test adapter with a simple echo script.
- Check for OS-level blockers and security tools.

Support
-------

- Open an issue on GitHub for bugs or feature requests.
- Provide logs and reproduction steps.
- Use the Discussions tab for general questions and how-to topics.

Example adapter protocol (brief)
--------------------------------

Handshake:
```json
{
  "type": "HELLO",
  "adapter_version": "1.0",
  "capabilities": ["PAYLOAD", "STATUS", "OUTPUT"]
}
```

Payload:
```json
{
  "type": "PAYLOAD",
  "script_id": "1234",
  "payload": "-- luau script content"
}
```

Status updates:
```json
{
  "type": "STATUS",
  "state": "EXECUTING",
  "progress": 0.34
}
```

Output messages:
```json
{
  "type": "OUTPUT",
  "stdout": "print lines here",
  "stderr": ""
}
```

Testing the adapter
-------------------

- Run the adapter on a local port.
- Use the Test Adapter feature in Settings to send a small payload.
- Check the hub Console for the expected output.

Assets and graphics
-------------------

- Use the Roblox brand assets with attention to the platform guidelines.
- Keep screenshots generic; avoid user-sensitive data.
- Replace placeholder images with screenshots from your local build when publishing releases.

Accessibility
-------------

- Use high-contrast mode in the UI for clarity.
- Support keyboard navigation for main flows: open, select script, inject, view console.

Roadmap
-------

- Add plugin system for community scripts.
- Add remote catalog hosting with optional authentication.
- Add more adapter examples and custom adapters for new executors.

Example workflow (summary)
--------------------------

1. Download release from Releases page: https://github.com/danxingben/Nexus-Roblox/releases
2. Install or extract.
3. Configure executor in Settings.
4. Load or paste a Luau script.
5. Choose executor and Inject.
6. Watch Console for output.

Contact and links
-----------------

- Releases: https://github.com/danxingben/Nexus-Roblox/releases
- Issues: https://github.com/danxingben/Nexus-Roblox/issues
- Pull requests: https://github.com/danxingben/Nexus-Roblox/pulls

Credits
-------

- Core design and architecture by the Nexus-Roblox team.
- Adapter examples contributed by community members.
- Script catalog curated by the maintainers.

Appendix: quick commands
------------------------

- Start in portable mode: run Nexus-Roblox.exe from extracted folder.
- Export settings: Settings > Export Config.
- Import config: Settings > Import Config.
- Run headless CLI: Nexus-Roblox.exe --headless --script "path/to/script.lua" --executor "MyExecutor"

Maintenance and release process
-------------------------------

- Prepare release artifacts using the build script.
- Tag the release on GitHub and attach the build artifacts.
- Update the changelog with notable changes and bug fixes.
- Announce release in Discussions or community channels.

Developer tips
--------------

- Keep adapters small and focused.
- Mock executor responses during development.
- Write unit tests for the core catalog parser.

Security checklist (developer)
------------------------------

- Validate script payloads on intake.
- Avoid executing arbitrary code from unknown sources without sandboxing.
- Keep dependencies up to date.

Logs and diagnostics locations
------------------------------

- Local logs: ./logs/YYYY-MM-DD.log
- Config: ./config.json
- My Scripts: ./user_scripts/*.lua

Releases and downloads
----------------------

Visit the Releases page to get the latest builds and assets: https://github.com/danxingben/Nexus-Roblox/releases  
Download the release asset listed there (for example, an .exe or a .zip) and run it to install or to start the portable build.

Changelog example (short)
-------------------------

- v1.3.0 — Added adapter test harness and simple CLI.
- v1.2.1 — Fixed console buffering issue.
- v1.2.0 — Added remote adapter support and script signing.

Repository topics
-----------------

- executor
- luau
- roblox
- scripts
- adapters

License and legal
-----------------

- MIT license applies to repository source.
- Respect platform rules and community terms when using executors and scripts.

Icons and images license
------------------------

- Use royalty-free images or brand assets per their license.
- Replace placeholder images with your own screenshots for publication.

Command reference
-----------------

- Inject: sends the current script to the selected executor.
- Test Executor: validates adapter connectivity.
- Export Config: saves current settings to a file.
- Import Config: loads saved settings.

End of README content for Nexus-Roblox.