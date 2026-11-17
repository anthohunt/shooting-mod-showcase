**English** · [Français](README.fr.md)

# mod tournage

**A Claude Code mod that turns a scenario into a narrated demo video: one agent per sequence films the real app or animates a diagram, at the pace of a synthetic voice, and reviewers comment on a shared editing table.**

[![The online editing table in use: an animated explainer, clips of a VR game, a timestamped comment and a comment on the script (click for the full video)](docs/demo.gif)](https://drive.google.com/file/d/1SZoBrUY1-yUUj2OjwhjZSsK4-osTDg5U/view)

*The online editing table in use: an animated explainer made with the mod, then clips of a VR game, a comment at the exact instant and a comment on the script. Interface in French. [Full video (1:49)](https://drive.google.com/file/d/1SZoBrUY1-yUUj2OjwhjZSsK4-osTDg5U/view)*

## Using it

- **Scenario.** `/tournage <demo>` opens the project and Claude writes the scenario, sequence by sequence. A title ending in « · filmée » is filmed on the app; the others are animated.
- **Voice first.** Each sequence is read in a single edge-tts take. Pauses come from punctuation and from what the picture needs; above 3.5 s, an alert instead of a pause.
- **One agent per sequence.** It films the app (web in Chrome, or a VR headset) or renders an SVG and GSAP animation frame by frame, at the pace of the voice.
- **Audit.** Each clip, then the assembled video, is checked for jumps, frozen shots, empty frames and silences before you see it.
- **Editing table.** Clips end to end, the script scrolling alongside. A comment marked « à traiter » sends only that sequence back to its agent. Versions V1, V2… keep their script and comments.
- **Online review.** One address per demo. Reviewers give a name, no account; their comments come back into the local table.

## Architecture

![mod tournage architecture: you approve the scenario; the lead session gives one agent per sequence; the voice sets the pace, the agent films or animates, the audit passes the clip to the editing table; the table is published to the online table on a VPS, reviewers comment there and the comments are brought back](docs/architecture.en.svg)

## Status

- **Since October 2026.** Built while making a 16-sequence demo of a supply-chain game, on the web and in VR (7 min 16).
- **Videos.** A 15 min 52 presentation of La Boucle and its English version (15 min 54), and a 4-minute English pitch.
- **Public tables.** [La Boucle, English pitch](https://montage.ingevision.cloud/la-boucle-en/) · [SuMo 2.0, VR game](https://montage.ingevision.cloud/sumo2-0/)
- **Where it runs.** The mod runs in Claude Code on the author's computer: 951 rendered frames per minute with 12 browsers, flat beyond, on a 32-thread laptop. The online table is a dependency-free Python server in a Docker container behind Traefik, on a VPS.
- **Stack.** Python 3, Node.js, Playwright, edge-tts, ffmpeg, SVG and GSAP.

---

**Anthony Hunt** · [ingevision.cloud](https://ingevision.cloud/?lang=en&p=mod-tournage) · [LinkedIn](https://www.linkedin.com/in/anthony-hunt-3948a9196) · [GitHub](https://github.com/anthohunt)

The code is private.
