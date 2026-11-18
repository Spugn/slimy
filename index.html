# Slimy Companion page

`index.html` is the computer-side half of Slimy's Screen OCR. It's a single static file with no build step and no external requests.

## How it works
1. The phone runs a Bluetooth LE GATT server (Screen OCR switch in the app).
2. This page connects to it with **Web Bluetooth** and shares a window with **getDisplayMedia**.
3. The phone asks for regions (`{"t":"cap", x, y, w, h, ...}` as window fractions). The page crops the latest frame, encodes it as JPEG/PNG and writes it back in chunks.
4. A heartbeat goes out every second from a Web Worker, so it isn't throttled when the tab is in the background. If the shared window closes, the page sends `ENDED` and the phone stops any macro that needs Screen OCR.

## Fast Wi-Fi mode
When the phone and the computer are on the same network, the phone also offers a **WebRTC DataChannel** over the Bluetooth link. The page answers over Bluetooth too, so no signaling server, STUN or TURN is involved and nothing leaves the local network. Once the channel opens, capture requests and images use it. That takes tens of milliseconds instead of seconds, so the phone asks for full-resolution, higher-quality images, which OCR reads more accurately.

Bluetooth still carries the heartbeat and the "window closed" signal. If Wi-Fi drops, captures fall back to Bluetooth without stopping the macro, and the phone retries Wi-Fi later (right away after a network change). The page's **Link** stat shows which one is in use.

If Wi-Fi never connects on a network where both devices really are on the same LAN, check for "client isolation" / guest-network mode on the router, which blocks devices from reaching each other.

The wire format is documented in `app/src/main/java/dev/spugn/slimy/vision/VisionProtocol.kt`.

## Hosting
Web Bluetooth and screen capture require a secure context, so serve the page over **https**. GitHub Pages works:

1. Create a repository (e.g. `slimy`) and add `index.html` at its root.
2. Go to **Settings → Pages**, deploy from the `main` branch, root folder.
3. Open `https://<user>.github.io/slimy/` in Chrome or Edge, and paste that URL into the app (Screen OCR → Companion page URL). The app can then type it into Chrome for you.

## Requirements
- Chrome or Edge (Web Bluetooth). Firefox and Safari don't support it.
- A computer Bluetooth adapter with Bluetooth LE (almost all built-in adapters from the last ~8 years).
