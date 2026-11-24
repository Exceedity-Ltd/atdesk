# Changelog

atdesk puts the Claude Code session already running in VS Code on your phone.
Versions number the service. The VS Code extension takes a new number only when it
changes, so its Marketplace copy can be behind.

## 0.3.29

- **The VS Code extension's Stop service row says what your service really
  does.** It now follows the version of the atdesk service installed on that
  computer. From 0.3.26 on a Mac and 0.3.25 on Windows it says the service
  stays stopped, across logins too, until you start it again. With an older
  service it says the service starts again at your next login on a Mac, or
  within a minute on Windows, and to update atdesk so that a stop holds. The
  update itself starts a stopped service again, so stop it once more afterwards
  if you want it off.
- **The two messages that tell you to run `atdesk update` now give a version,**
  as in `atdesk update 0.3.29`: without one, it only prints how to use it.
- **The extension's page says what matters first, and its privacy section is
  now true.** At its usual width, VS Code's Extensions view shows only about
  the first thirty characters of an extension's description, so atdesk's now
  opens with the price and that it installs a service. The extension's page, on
  the Marketplace and in VS Code, said there was no account and no password and
  no third-party scripts on our site, and listed less than we hold. It now says
  atdesk itself has no account or password, while the free Kanban board that
  comes with a subscription, at kanban.atdesk.io, has both if you make one;
  lists what we hold for each computer, and that we hold a hash of your
  subscription id; names the one small script Cloudflare adds to atdesk.io; and
  points to the privacy notice for the rest.
- **A consult reaches a conversation whose turn has finished.** When the
  /atdesk-consult or /atdesk-handover skill sends a message to another
  conversation on this computer (`atdesk ask-session --send`), and all Claude
  Code wrote after that conversation's last turn is a background task's notice
  that starts no turn (newer Claude Code versions write some this way), the
  message now goes in. Before, it was left in that conversation's message box
  until someone pressed Enter at the computer. It now also refuses a
  conversation where a message someone typed there has not gone in yet, since a
  turn is about to start, and its refusal says the send could land in a turn
  that is running or about to start. As before, a refused send is left in that
  conversation's message box for you to send or clear.
- **Corrections to earlier notes.** 0.3.27 said its Stop service row says the
  service stays stopped once `atdesk update` has run. The row said so as soon
  as the extension updated, and it was true only with a service of 0.3.26 or
  later on a Mac, or 0.3.25 or later on Windows: before that, a stopped service
  came back at the next login on a Mac and within a minute on Windows. 0.3.27's
  "The README lists four things setup leaves to you" meant the README that
  comes with the service, in its install folder, not the extension's page on
  the Marketplace. And 0.3.25 said the VS Code extension was unchanged, but one
  line of its README had changed, to say there is nothing to download from the
  App Store; the Marketplace copy took that line in 0.3.27.
- **Updating:** run `atdesk update 0.3.29` in a terminal, on a Mac and on
  Windows. If you had stopped the service with `atdesk stop`, the update starts
  it again; stop it once more and it stays stopped, across logins too. If you
  have the atdesk skills installed and are on 0.3.24 or older, run `atdesk
  skills` once afterwards; from 0.3.25 the update keeps them current. The VS
  Code extension changes too: a copy installed from the Marketplace updates to
  0.3.29 by itself, whether or not you have run the update. If atdesk linked
  the extension for you, reload the VS Code window after the update to load it.

## 0.3.28

- **Claude can run one command as root on your Mac, with your yes and your
  password.** With the atdesk skills installed, `atdesk sudo -- <command>` runs
  one command as root, in `/`, so Claude names every file by its full path.
  Claude Code asks you first, showing the command, with auto mode on too. Then
  macOS opens its own password box on the Mac, which on macOS 27 names no
  command, only "a script started by node", and your password goes only to
  macOS. One box comes within seconds of your yes; a box at any other time is
  not atdesk's, so press Don't Allow. The password is typed at the Mac: you can
  approve from your phone, but with nobody at the Mac the box closes after 100
  seconds and nothing runs. A command that fails shows its error output and
  status, not its other output. A command over 200 characters, or holding a
  tab, a line break, an invisible character or two spaces in a row, is refused,
  so the prompt shows exactly what runs. The new atdesk-sudo skill tells Claude
  to warn you first and to wait if you are away. macOS only: elsewhere
  `atdesk sudo` refuses, though the skill is installed with the others.
- **The consult gate guards it.** The consult gate, the hook `atdesk skills`
  registers, refuses every other spelling of `atdesk sudo` it recognises
  (though not a command built in pieces or run from a script), and any command
  that names atdesk or vsr together with the word sudo, a search or a commit
  message included: Claude writes those another way. Your own `sudo` is left
  alone in a command that names neither. `atdesk sudo` refuses while your own
  or the project's Claude Code settings switch hooks off.
- **Your own phones get back in when your computer's connections are full.**
  atdesk on your computer now tells the relay, as each paired phone's handshake
  completes, that the connection is yours. So when one stranger who has seen
  your pairing QR or install line keeps your computer's eight connections full,
  the relay ends one of theirs rather than a phone already connected.
- **Updating:** run `atdesk update 0.3.28`, on a Mac and on Windows. The
  version is required: the notes for 0.3.24 to 0.3.27 said `atdesk update`
  alone, which only prints how to use it. If you have the atdesk skills
  installed and are on 0.3.25 or later, the update adds the atdesk-sudo skill
  too; from 0.3.24 or older, run `atdesk skills` once afterwards. The VS Code
  extension is unchanged, so the Marketplace stays at 0.3.27.

## 0.3.27

- **A workflow waiting for your approval stays on your phone.** While one of a
  workflow's agents waits for your permission, your phone keeps the run's agents
  line, its working bar and its row on the board, however long the approval
  waits while your computer is awake with that conversation open in VS Code,
  and also after you open that conversation on your phone. Before, a wait of
  more than 45 minutes made the run vanish from your phone and buzzed "turn
  finished" in the middle of it. A run that falls quiet shows again as soon as
  its agents write.
- **Starting a conversation works on a slower Mac.** Starting a conversation
  from your phone, or with `atdesk new-session`, now takes its new tab even once
  Claude Code shows that tab's own session id, so a Mac slow to list its tabs no
  longer fails with an empty tab left open ("VS Code did not open a new tab" on
  your phone, "no new panel appeared" from `atdesk new-session`).
- **Two starts never share a tab.** When your phone and `atdesk new-session`, or
  two sessions, start conversations in the same VS Code window at nearly the
  same moment, each one types only into the new tab it found and claimed.
- **Pairing two Macs both ways asks before re-pairing.** Asked to pair two Macs
  both ways, a Claude session checks each direction already paired with
  `atdesk link list`, tells you which one already works and asks before
  re-pairing it, and has an old key revoked only in the other Mac's own
  terminal.
- **The README lists four things setup leaves to you,** the atdesk skills and
  their two gates among them, and says what declining the skills leaves.
- **Updating:** `atdesk update` is all you need, on a Mac and on Windows. From
  0.3.25 or later it also updates the atdesk skills you have installed, the
  atdesk-link skill's new pairing steps included; from 0.3.24 or older, run
  `atdesk skills` once afterwards. The VS Code extension installed from the
  Marketplace updates to 0.3.27 as well, from 0.3.21: once `atdesk update` has
  run on that computer, its Stop service row says the service stays stopped,
  across logins too, until you start it again, and its README says there is
  nothing to download from the App Store.

## 0.3.26

- **Reach the conversations on your other Mac.** Pair two Macs that both run
  atdesk with `atdesk link pair`, once in each direction, with the link taken
  off the clipboard rather than passed through a conversation. A Claude session
  in any project on one Mac can then list, read and send to the conversations
  on the other with `atdesk link`. It needs the atdesk skills (`atdesk skills`)
  on both Macs: their gate asks you before every send, and each message arrives
  with a first line saying a Claude session on another Mac typed it. The new
  atdesk-link skill tells Claude how; it is for Macs.
- **See a workflow's agents on your phone.** While Claude runs a workflow, your
  phone shows how many of its agents are working, whether one is waiting for
  your permission and whether one failed, and the conversation stays busy until
  the run ends.
- **Buzzes you were missing.** A question Claude asks straight after an
  approval now buzzes your phone once that conversation's 20-second gap ends,
  as does one asked before you turned notifications on, or whose first buzz
  failed; before, none of these ever buzzed. A computer whose folder has no
  conversation yet buzzes for your other open conversations too. A "your turn"
  buzz is no longer lost when your computer stalls, and atdesk restarting no
  longer buzzes you for a reply you have already read.
- **Conversations named as you would name them.** A conversation started in a
  folder whose name has a hyphen, such as `~/Projects/my-app`, is called my-app
  on your phone, not app; on a Mac, a folder inside Desktop, Documents,
  Downloads or Library still shows the part after its last hyphen. With Claude
  in Chrome connected, a conversation Claude Code names after Chrome's
  instruction is shown on your phone by the first message you typed, and the
  chat shows your message rather than that instruction.
- **On a Mac, `atdesk stop` keeps the service stopped**, across logins too,
  until you start it again, as on Windows; `status` and `setup --check` say
  so, and a second `atdesk start` says the service is already running.
- **The right commands and the right computer.** Your phone and atdesk's own
  messages tell you to run `atdesk pair` and `atdesk status`, never the old
  `vsr` or `vsrd`, and every pairing or connection failure says "the
  computer", not "the Mac".
- **The gates ask in more cases.** A repository you clone can no longer start
  an agent of its own under the name of Claude Code's read-only search helper
  without your yes. A send between sessions asks however it is written,
  including with a backtick, a continued line or one of `; | & ( ) >`.
- **Updating:** `atdesk update` is all you need, on a Mac and on Windows. From
  0.3.25 it also adds the atdesk-link skill when you have the atdesk skills;
  from 0.3.24 or older, run `atdesk skills` once afterwards. While the new
  service starts, the update says in a plain line that it is not answering yet,
  then that the update worked. If you had stopped the service with
  `atdesk stop`, this update starts it again. If atdesk linked the VS Code
  extension for you, reload the VS Code window to load its new Stop service
  row, which says the service stays stopped until you start it; a copy
  installed from the Marketplace stays at 0.3.21.

## 0.3.25

- **Every conversation on your computer can reach your phone.** Approvals,
  Claude's questions and "your turn" now buzz your phone from every
  conversation open in VS Code, not only the one your phone follows. Each one
  shows as a line above the conversation you are reading: answer an approval
  or a question right there, or tap a "your turn" line to open that
  conversation. A conversation you muted stays silent and shows no line.
- **Answer Claude's questions from your phone.** When Claude asks you
  something, your phone shows every question in one sheet: pick an answer,
  tick several, or type your own, then send them all with one Submit, or
  cancel the question.
- **An approval stays with its own conversation.** When your computer moves
  to another conversation, your phone drops the approval it was showing for
  the one it left, and shows the new conversation's at once.
- **A message goes only where you wrote it.** If your computer has moved to
  another conversation since your phone last showed it, a message you send is
  refused, with nothing typed, instead of landing in the other conversation.
- **Windows: `atdesk stop` keeps the service stopped**, across logons too,
  until `atdesk start`. On a Mac, `stop` and `status` now say that the service
  comes back at your next login.
- **`atdesk update --dry-run` on Windows** names the two scheduled tasks it
  would repoint, instead of launchd jobs that Windows does not have.
- **Updating:** `atdesk update` is all you need, on a Mac and on Windows.
  From the update after this one, an update also rewrites the `atdesk` and
  `vsr` commands in the new version's own words. The VS Code extension is
  unchanged, so its Marketplace copy stays at 0.3.21.

## 0.3.24

- **"Start something new" finds your projects wherever they are.** It lists
  the folders open in VS Code and the folders where you have had Claude Code
  conversations, as well as your projects folder, so a computer with no
  `~/Projects` (most Windows machines) shows its projects instead of an error.
  It also lists a folder whose path has a dot, a space or an accent in it (such
  as `C:\Users\<first>.<last>\app`), and follows and counts its conversations, and
  a folder whose first conversation began with a pasted screenshot. Your
  temporary folder is no longer listed as a project.
- **"Switch conversation" offers your closed projects too:** each one's last
  conversation, newest first, beside the open ones. Pick one and your computer
  opens the project and carries on in that conversation.
- **Windows: the atdesk skills now work inside Claude Code**, whose Bash tool
  could not find `atdesk` or `vsr`.
- **`atdesk status` and the checks say what is wrong and which step fixes
  it**, and looking no longer sets anything up: `status`, `help`,
  `skills --check` and `setup --check` create nothing on a computer where
  atdesk was never set up.
- **The consult gate asks in more cases**, including a send that puts quotes
  around `--send` or `--session`.
- **Updating:** on a Mac, `atdesk update` is all you need. On Windows, run
  `atdesk skills` once afterwards, in PowerShell or Command Prompt: this update
  is applied by the version you had, which does not set up the new commands,
  and the next update does it for you. The VS Code extension is unchanged, so
  its Marketplace copy stays at 0.3.21.

## 0.3.23

- **Start a new conversation from your phone, in any of your projects.**
  "Start something new" lists the folders in your projects folder, open ones
  first. That is `~/Projects` unless you choose another: in VS Code, run
  "atdesk: Set the projects folder" from the Command Palette. Pick one and type
  the first message: your computer opens the project if it needs to, starts a
  new conversation in a new tab of that project's window, and sends your
  message there. Since 0.3.5 this was refused every time.
- **Agents wait for your yes.** After `atdesk skills`, every workflow and every
  agent a session starts, except the read-only search helper, waits until you
  say yes, at the desk or on your phone, so nothing spends your usage on agents
  without asking. A session that nobody is watching stops at the first one and
  waits. `atdesk skills --remove` takes it out again, with the other atdesk
  skills.
- **The atdesk-ultracode skill**, installed by `atdesk skills`, tells a session
  when many agents are worth it, and to do the rest itself.
- **"Your turn" means there is something new to read.** A session running
  background tasks used to buzz your phone again for a reply you had already
  read, each time a task reported in. Your phone now buzzes once per new reply.
- **`atdesk new-session` types only into the tab it opened.** If VS Code
  restored a tab at the same moment, in that window or another, the first
  message could go into it. It now waits for the new, empty tab in the window it
  clicked, and refuses a tab that already holds a conversation.
- **Windows: conversations in your temporary folder stay off your phone's
  project list**, as they already did on a Mac.
- `atdesk update` does not refresh skills you already installed: run
  `atdesk skills` once after updating. The VS Code extension itself is
  unchanged, so its Marketplace copy stays at 0.3.21.

## 0.3.22

- **Each tool call appears once on your phone.** Claude Code 2.1.300 and later
  write a copy of most requests into the session's history, and atdesk showed
  the copies too: tool calls arrived twice, and a session still waiting on
  Claude could look finished. The copies are now ignored.
- **A computer that sleeps while reconnecting comes back by itself.** If your
  computer went to sleep in the middle of reconnecting to atdesk, it could stay
  offline for days. A connection attempt that gets no answer within 20 seconds
  is now abandoned and retried. The check that `atdesk setup` and
  `atdesk update` finish with has the same limit, so it can no longer hang.
- **Approvals for background agents reach your phone.** While a workflow or a
  background agent waited for your approval, nothing reached the phone, and
  every message you sent from it was refused because a dialog was open. Those
  prompts now reach the phone like any other. A tap answers only the prompt you
  were shown: if it has changed, nothing is clicked and the phone shows the
  current one.
- **What you are typing at your desk is never typed over.** If the session's
  message box already holds text nobody has sent, a message from the phone is
  not typed into it. The phone tells you how many characters are there, and
  lets you replace them or cancel.
- **A stopped turn reads as finished.** After you press Stop, at the desk or on
  the phone, the session shows as finished straight away, instead of "working"
  for up to five minutes.
- **A send says what actually happened.** atdesk presses Enter only when the
  message box holds exactly your text, so a key pressed at the desk at the same
  moment is not sent glued to your message. If it cannot confirm the message
  went, the phone says so instead of reporting success.
- **The `/atdesk-consult` and `/atdesk-handover` skills** now explain every
  result `atdesk ask-session` and `atdesk new-session` can report, and which
  ones must not be retried; `atdesk peer tail` no longer drops a short
  session's first message. `atdesk update` does not refresh skills you already
  installed: run `atdesk skills` once after updating.
- The VS Code extension itself is unchanged, so its Marketplace copy stays at
  0.3.21.

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
