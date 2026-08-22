# Changelog

atdesk puts the Claude Code session already running in VS Code on your phone.
Versions are the service and the extension together — they ship as one number.

## 0.3.21

- **Nothing you can see changed.** A comment inside the published package named
  the developer personally. A published version can never be withdrawn, so it is
  removed before this one ships, and a check now refuses to publish bytes that
  name whoever built them.

## 0.3.20

- **Cancelling "Check this computer" no longer reports a broken network.** Backing
  out of the check told you atdesk could not be reached, and advised you to sort
  out your proxy "before you pay" — a diagnosis of nothing but your own decision to
  press Cancel. It now stops quietly and decides nothing, which is what cancelling
  the activation lookup has always done.
- **A refusal no longer gives you the same advice twice.** When atdesk cannot look
  your code up, its message already tells you to paste the full install command
  from your email; a second sentence then said the same thing again in different
  words.

## 0.3.19

- **Paste your activation code, not a `curl` command.** The install step now asks
  atdesk which release your code entitles you to, shows you the exact command it
  is about to run, and runs it only after you say yes. Your welcome page already
  told you it would ask for the code; now it does. Pasting the whole command still
  works, so a code you cannot look up is never a dead end.
- **"Check this computer" now checks it can reach atdesk**, before you pay rather
  than after. Behind a corporate proxy that was the one requirement you could only
  discover once your money and your code were spent.
- **The walkthrough no longer tells a paying customer to start a trial.** If you
  arrived with a code, that step is answered.
- **"Bring that window forward" stops claiming a window is gone when it is not.**
  On Windows Terminal — the Windows 11 default — the title a program sets is not
  the title the window shows, so the button reported "no atdesk window" to people
  watching setup run. It now says where setup is, and that Windows Terminal keeps
  several sessions in one window as tabs, which nothing can raise from outside.
- **A code that is already used or expired now offers help** instead of only
  offering to retype the same code, which could never work.
- Three messages carried explanatory text that VS Code only ever renders in a
  modal dialog, so nobody had read it. It is now in the message.

## 0.3.18

- **"Bring that window forward" now tells you what it found.** It could always
  raise the window while setup was running; clicked after setup had finished there
  was nothing named atdesk to raise, and it said nothing at all. It now says so.

## 0.3.17

- **"Bring that window forward" now works.** The button matched a window title
  that only existed when the extension had opened the terminal — so copying the
  install command and running it yourself, which is what the walkthrough tells you
  to do, left the button with nothing to find. The installer and setup now name
  their own window.
- **Setup no longer ends by saying a working install is broken.** It re-checked
  the extension at the moment the debugging port opened, which is earlier than the
  extension starts, and then carried that stale answer into the summary.
- Windows: the shim line no longer prints mixed `\` and `/` separators.
- An old skill directory left by a rename now says the command to remove it,
  rather than "remove it by hand".

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
