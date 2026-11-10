# Cinola — releases

Builds of Cinola, a macOS client for Jellyfin. The app updates itself from here (Sparkle);
this repository only holds the update feed (`appcast.xml`) and the release archives.

## Install (first time)

Requires a Mac with Apple Silicon and macOS 27.

1. Download the latest `Cinola-x.y.z.zip` from [Releases](../../releases) and unzip it.
2. Move `Cinola.app` to Applications.
3. The app isn't notarized yet, so macOS blocks it until you run this once in Terminal:

   ```
   xattr -dr com.apple.quarantine /Applications/Cinola.app
   ```

4. Open Cinola, enter your Jellyfin server address and sign in.

After that, new versions arrive by themselves (Cinola → «Проверить обновления…»).

## Open-source components

Cinola is built on open-source components; their licenses are listed in the app
(Settings → General → Acknowledgements).

The playback engine, [AetherEngine](https://github.com/superuser404notfound/AetherEngine)
(LGPL-3.0 with an App Store exception), ships as its own framework inside the app and can be replaced.
Cinola uses a modified copy of it (a hook for Headphone Surround, a subtitle prefetcher that stays
idle while the video buffer already covers it, and a second connection that fetches the next range
while playback can't keep up). The complete source of that copy is attached to each release as
`AetherEngine-<version>-cinola-source.tar.gz`; `PATCHES.md` inside lists every change from upstream.

Cinola was previously called BondMedia.
