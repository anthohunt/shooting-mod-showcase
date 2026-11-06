**English** · [Français](README.fr.md)

**Anthony Hunt** · [Project page on ingevision.cloud](https://ingevision.cloud/?lang=en&p=mod-tournage) · [LinkedIn](https://www.linkedin.com/in/anthony-hunt-3948a9196) · [GitHub profile](https://github.com/anthohunt)

> Showcase repository: the code and data of this project are private; this README describes it.

# Demo video mod

A module for a command-line coding assistant that produces demo videos narrated by a synthetic voice, either filmed on the real application or animated.

## The problem

A demo video means writing a text, recording it, filming the application at the right pace, then editing it all together. Everything has to be redone for each version of the software. The mod hands these tasks to agents and keeps the author in charge: they approve the script, watch the video and correct it. It is used for software demos and project presentations.

## How it works

- **Script**: the agent looks at the application and writes the script sequence by sequence. A title ending in "· filmed" is shot on the application; the other sequences are animated.
- **Filming**: one sequence per agent. Filmed sequence: the agent rehearses, then films the application (web or VR headset) at the pace of the voice. Animated sequence: an animated SVG infographic, rendered frame by frame.
- **Voice**: the whole narration of a sequence is read in a single take. Pauses start from punctuation (about 1 s between two sentences, 0.35 s on a comma) and grow longer when the picture needs time, up to 3.5 s; beyond that, an alert.
- **Check**: each clip, then the assembled video, goes through an audit (jumps, frozen shots, empty frames, silences) before being shown.
- **Editing table**: the clips end to end, the script scrolling along with the spoken word highlighted, timestamped comments. A correction sends the sequence back to filming.

## What is built

- In service, in two steps: script, then filming.
- Online editing table: each demo has its own address, reviewers comment under their name, without an account (30 comments per 10-minute window, 2,000 characters each).
- Frozen versions (V1, V2…): each version keeps its script and its comments.
- Style of animated sequences: a style guide drawn from the analysis of 20 explainer videos, with 16 checkable rules; each sequence is critiqued by a fresh agent.
- Parallel rendering across several browsers: 951 frames per minute with 12 browsers, flat beyond that, on a 32-thread laptop.
- Videos produced: a 16-sequence demo (7 min 16) and the presentation "Le mode La boucle" (15 min 52). The videos on this site are made with this mod.

## What is public

The editing table of an English video is visible: <https://montage.ingevision.cloud/la-boucle-en/>. The mod's code stays in a private repository.

## Tech stack

- Python 3 (tools, online editing table server in a Docker container)
- Node.js (frame-by-frame rendering and voice generation)
- edge-tts (synthetic voice)
- ffmpeg and ffprobe
- Google Chrome (rehearsing and filming web demos)
- SVG and GSAP (animations)
