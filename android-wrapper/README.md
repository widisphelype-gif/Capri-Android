# Capri Android (experimental)

This folder adds an Android client shell for Capri. It does **not** port the desktop/CLI runtime to Android: the original Capri project depends on desktop/Node/Bun capabilities (including terminal process support) that are not available as-is in an ordinary Android WebView.

## What this build does

- Provides a dark, neon Capri-branded Android entry screen.
- Lets the user enter the URL of a Capri server they control.
- Loads the server UI inside the app when the server allows embedding.
- Builds a debug APK through GitHub Actions.

A Capri backend must already be running on a computer or server and reachable from the phone. This APK does not run the Capri coding agent locally. Some servers may block iframe embedding through their security headers; in that case, a dedicated Android-compatible client/server integration is still needed.

## Build

The workflow `.github/workflows/android-apk.yml` builds on pushes to `android/mobile-apk` and can also be started manually from the Actions tab (if Actions are enabled for this fork).

After a successful run, download the `capri-android-debug` artifact from the workflow run. Extract the ZIP to get `app-debug.apk`.

## Safety and privacy

- Use a server URL you trust.
- Prefer HTTPS for any server outside the same device.
- The wrapper does not ask for or store Capri credentials in its connection screen.
- The upstream desktop cyberpsychosis/sabotage feature is not included in this Android shell.
