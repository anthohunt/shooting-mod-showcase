[English](README.md) · **Français**

**Anthony Hunt** · [Fiche du projet sur ingevision.cloud](https://ingevision.cloud/?p=mod-tournage) · [LinkedIn](https://www.linkedin.com/in/anthony-hunt-3948a9196) · [Profil GitHub](https://github.com/anthohunt)

> Dépôt vitrine : le code et les données de ce projet sont privés ; ce README le décrit.

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
