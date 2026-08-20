# Changelog

atdesk puts the Claude Code session already running in VS Code on your phone.
Versions are the service and the extension together — they ship as one number.

## 0.3.16

- The setup walkthrough now **moves on by itself** as each step completes. VS Code
  does not do this on its own, so finishing a step used to leave you looking at the
  thing you had just done.
- When setup is waiting for you in a terminal, the message says **where it is**
  rather than describing which window title the extension was hunting for.
- The installer and setup now call the product **atdesk** in their first line.
  They still said `vscode_remote`, which is the old internal name.
- Windows: the pairing screen says **"This machine is …"** rather than "This Mac".
  It is the screen where you confirm a fingerprint, so it should not name a
  computer you do not own.
- The status bar reads **atdesk** rather than the retired "Remote" when no Claude
  Code session is open in the window.
- Stopping the service no longer reports "Service stoped."
- The README is clearer that **approvals and switching project**, not only typing,
  need VS Code's local debugging port — and that the service starts at login.

## 0.3.15

- The extension finds a separately-installed service through the background
  service's own registration, so a Marketplace install on a machine that already
  has atdesk stops showing "Get started" when it is in fact ready.
- Walkthrough steps complete on measured state rather than on having clicked.

## 0.3.14

- The Marketplace extension shows a status bar entry and a six-step walkthrough on
  a machine with no service installed, instead of appearing to do nothing.

## 0.3.13

- Setup survives quitting VS Code: the installer runs in a terminal window outside
  the editor, because setup asks you to quit it partway through.

## Earlier

0.3.0–0.3.12 were private releases. The service, the relay transport, Windows
support, signed releases and the phone app were built across them.
