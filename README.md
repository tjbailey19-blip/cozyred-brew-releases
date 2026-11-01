# Brew releases

What Brew.app reads from the internet, and nothing else. No code lives here.

- `appcast.xml`: the update feed Brew checks once a day (Sparkle). Each version's notarized zip is an asset of its GitHub release, signed with Brew's update key.
- `notes/`: each version's release notes.
- `revoked.json`: the invite codes that are turned off, signed with Brew's invite key. Brew downloads it with a plain request that sends nothing about you or your projects.

## Getting started

**What Brew needs.** A Mac with Apple silicon, macOS 14 or later, Adobe Premiere Pro 25.6 or later, and 10 GB free. An internet connection the first time it opens (it downloads the transcription model, about 1.6 GB, once) and whenever it reads a recording with Claude. Your recordings never leave your Mac; only the words of the transcript go to Anthropic, under your own key.

**Two things to have ready.**
- A Claude key. Sign in at https://console.anthropic.com, open API keys, make a key (it starts with `sk-ant-`) and put credit on the account there. Brew keeps the key in your Mac's Keychain and uses it only for your own requests.
- Your invite code, the one you were sent with this link. Paste the whole code.

**Install.** Download the newest `Brew-<version>.zip` from this repository's Releases page, double-click it to unzip, drag Brew into your Applications folder, and open it from there (opened from Downloads, Brew asks to be moved first). macOS asks once whether to open an app downloaded from the internet. Brew has no window: a cup appears in the menu bar at the top right of the screen. Its first screen checks your Mac, downloads the model, and asks for your Claude key and your invite code; press Keep.

**Where the panel is.** Brew puts its own panel into Premiere Pro. Open Premiere and a project, then open the panel from Window → UXP Plugins → Brew and press Choose your episode folder. After your first episode, with Premiere closed, Brew docks the panel beside the timeline for the next time. In the panel: Choose your episode folder, wait for the ready shorts, and click one to put it in your timeline; or pick a beat and press Make the cut.

**Uninstall.** Click the cup in the menu bar and choose Uninstall Brew…: Brew moves itself to the Trash, takes its panel out of Premiere and forgets your Claude key. Uninstall and Remove Projects deletes its data folder too.
