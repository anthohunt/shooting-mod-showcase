[English](README.md) · **Français**

# mod tournage

**Un mod de Claude Code qui fait d'un scénario une vidéo de démonstration commentée, filmée sur la vraie application ou animée, et relue sur une table de montage partagée.**

[![La table de montage en ligne en usage : une vidéo animée, des clips d'un jeu VR, un commentaire horodaté et un commentaire sur le script (version anglaise, cliquer pour la vidéo complète)](docs/demo.webp)](https://drive.google.com/file/d/1SZoBrUY1-yUUj2OjwhjZSsK4-osTDg5U/view)

<details><summary>Version française</summary>

[![La table de montage en ligne en usage : une vidéo animée, des clips d'un jeu VR, un commentaire horodaté et un commentaire sur le script (cliquer pour la vidéo complète)](docs/demo.fr.webp)](https://drive.google.com/file/d/1aDX09CIwpQKxhxKWtaKRUQkpE0sdikNK/view)

</details>

*La table de montage en ligne en usage. [Vidéo complète (1:49)](https://drive.google.com/file/d/1aDX09CIwpQKxhxKWtaKRUQkpE0sdikNK/view)*

## Ce qu'on fait avec

- **Scénario.** `/tournage <démo>` ouvre le projet et Claude écrit le scénario, séquence par séquence. Un titre qui finit par « · filmée » se tourne sur l'application ; les autres sont animées.
- **La voix d'abord.** Chaque séquence est lue en une seule prise edge-tts, qui donne le rythme des images. Les pauses viennent de la ponctuation et de ce dont l'image a besoin ; une pause de plus de 3,5 s n'est pas appliquée, une alerte la signale.
- **Un agent par séquence.** Il filme l'application (web dans Chrome, ou casque VR) ou rend une animation SVG et GSAP image par image.
- **Audit.** Chaque clip, puis la vidéo assemblée, est contrôlé (sauts, plans figés, images vides, silences) avant d'être montré.
- **Table de montage.** Les clips bout à bout, le script qui défile à côté. Un commentaire « à traiter » renvoie seulement sa séquence à son agent. Les versions V1, V2… gardent leur script et leurs commentaires.
- **Relecture en ligne.** Une adresse par démo. Les relecteurs donnent un nom, sans compte ; leurs commentaires reviennent dans la table locale.

## Architecture

![Architecture du mod tournage : vous validez le scénario ; la session chef confie une séquence par agent ; la voix donne le rythme, l'agent filme ou anime, l'audit valide le clip pour la table de montage ; la table est mise en ligne sur un VPS, les relecteurs y commentent et les commentaires sont rapatriés](docs/architecture.svg)

<details><summary>Diagramme en français</summary>

![Architecture du mod tournage : vous validez le scénario ; la session chef confie une séquence par agent ; la voix donne le rythme, l'agent filme ou anime, l'audit valide le clip pour la table de montage ; la table est mise en ligne sur un VPS, les relecteurs y commentent et les commentaires sont rapatriés](docs/architecture.fr.svg)

</details>

## État

- **Depuis octobre 2026.** Construit en faisant une démo de 16 séquences de SuMo, un jeu de chaîne logistique sur le web et en VR (7 min 16, table privée).
- **Vidéos.** Une présentation de [La Boucle](https://github.com/anthohunt/la-boucle-module), la méthode de l'auteur pour confier une étape d'un processus à un petit modèle : [en français, 15 min 52](https://drive.google.com/file/d/1TZXAxUeyCGkEj3yFR7hDBZXeerJQxmtA/view) · [en anglais, 15 min 54](https://drive.google.com/file/d/1B0ZIb4txHxiYe0JcUWBq3rJRpRpqhCxr/view).
- **Tables publiques.** [La Boucle, version anglaise de 4 minutes](https://montage.ingevision.cloud/la-boucle-en/) · [SuMo 2.0, refonte VR (4 clips)](https://montage.ingevision.cloud/sumo2-0/)
- **Où ça tourne.** Claude Code sur le portable de l'auteur (banc de 600 images : 951 images par minute avec 12 navigateurs, plateau au-delà). La table en ligne est un serveur Python sans dépendance, sur un VPS.
- **Outils.** Python 3, Node.js, Playwright, Chrome, edge-tts, ffmpeg, SVG et GSAP.
- **Code.** Privé.

---

**Anthony Hunt** · [ingevision.cloud](https://ingevision.cloud/?p=mod-tournage) · [LinkedIn](https://www.linkedin.com/in/anthony-hunt-3948a9196) · [GitHub](https://github.com/anthohunt)
