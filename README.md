> Showcase repository: the code and data of this project are private; this README describes it. / Dépôt vitrine : le code et les données de ce projet sont privés ; ce README le décrit.

# Filming mod

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

---

## Version française

# Mod tournage

Un module pour un assistant de programmation en ligne de commande, qui fabrique des vidéos de démonstration commentées par une voix de synthèse, filmées sur l'application réelle ou animées.

## Le problème

Une vidéo de démonstration demande d'écrire un texte, de l'enregistrer, de filmer l'application au bon rythme, puis de monter le tout. Tout est à refaire à chaque version du logiciel. Le mod confie ces tâches à des agents, et garde l'auteur aux commandes : il valide le scénario, regarde la vidéo et corrige. Il sert aux démos de logiciels et aux présentations de projets.

## Comment ça marche

- **Scénario** : l'agent regarde l'application et écrit le scénario séquence par séquence. Un titre qui finit par « · filmée » se tourne sur l'application, les autres séquences sont animées.
- **Tournage** : une séquence par agent. Séquence filmée : l'agent répète puis filme l'application (web ou casque VR) au rythme de la voix. Séquence animée : une infographie SVG animée, rendue image par image.
- **Voix** : toute la narration d'une séquence est lue en une seule prise. Les pauses partent de la ponctuation (environ 1 s entre deux phrases, 0,35 s sur une virgule) et s'allongent quand l'image a besoin de temps, jusqu'à 3,5 s ; au-delà, une alerte.
- **Contrôle** : chaque clip, puis la vidéo assemblée, passe un audit (sauts, plans figés, images vides, silences) avant d'être montré.
- **Table de montage** : les clips bout à bout, le script qui défile avec le mot prononcé surligné, des commentaires horodatés. Une correction renvoie la séquence au tournage.

## Ce qui est construit

- En service, en deux étapes : scénario, puis tournage.
- Table de montage en ligne : chaque démo a son adresse, les relecteurs commentent sous leur nom, sans compte (30 commentaires par tranche de 10 minutes, 2 000 signes chacun).
- Versions figées (V1, V2…) : chaque version garde son script et ses commentaires.
- Style des séquences animées : une bible tirée de l'analyse de 20 vidéos de vulgarisation, avec 16 règles vérifiables ; chaque séquence passe la critique d'un agent neuf.
- Rendu en parallèle sur plusieurs navigateurs : 951 images par minute avec 12 navigateurs, plateau au-delà, sur un portable à 32 fils.
- Vidéos produites : une démo de 16 séquences (7 min 16) et la présentation « Le mode La boucle » (15 min 52). Les vidéos de ce site sont faites avec ce mod.

## Ce qui est public

La table de montage d'une vidéo en anglais est visible : <https://montage.ingevision.cloud/la-boucle-en/>. Le code du mod reste dans un dépôt privé.

## Pile technique

- Python 3 (outils, serveur de la table en ligne dans un conteneur Docker)
- Node.js (rendu image par image et génération de la voix)
- edge-tts (voix de synthèse)
- ffmpeg et ffprobe
- Google Chrome (répétition et tournage des démos web)
- SVG et GSAP (animations)
