# Brew releases

What Brew.app reads from the internet, and nothing else. No code lives here.

- `appcast.xml`: the update feed Brew checks once a day (Sparkle). Each version's notarized zip is an asset of its GitHub release, signed with Brew's update key.
- `notes/`: each version's release notes.
- `revoked.json`: the invite codes that are turned off, signed with Brew's invite key. Brew downloads it with a plain request that sends nothing about you or your projects.
