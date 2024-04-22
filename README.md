# Calendrier Républicain pour Home Assistant

## Installation

Le fichier `calendrier-republicain.yaml` crée une série de ["template sensors"](https://www.home-assistant.io/docs/configuration/templating/). Pour l'utiliser, il suffit de créer un répertoire de rajouter les lignes suivantes à votre configuration:

```
template:
  - sensor: !include calendrier-republicain.yaml
```

Comme j'utilise plusieurs fichiers définissant des *template sensors*, je mets tous ceux-ci dans le même répertoire nommé `templates`

```
template:
  - sensor: !include_dir_merge_list templates/
```

## Entités crées:

Voici les entités crées par le fichier, avec les exemples qui s'affichent le 22 avril 2024:

 * `sensor.calendrier_republicain_an`: CCXXXII
 * `sensor.calendrier_republicain_date_complete`: Quartidi 4 Floréal (Aubépine)
 * `sensor.calendrier_republicain_date_debut`: 22/09/2023 (Date du 1 Vendémiaire de l'an en cours)
 * `sensor.calendrier_republicain_jour_de_la_decade`: Quartidi
 * `sensor.calendrier_republicain_jour_du_mois`: 4
 * `sensor.calendrier_republicain_mois`: Floréal
 * `sensor.calendrier_republicain_nom_du_jour`:	Aubépine

## Mode de calcul

J'utilise un mode de calcul simplifié qui ne tient pas entièrement compte des subtilités de calcul des années à 365 ou 366 jours ("sextiles" dans le calendrier républicain, "bissextiles" dans le grégorien).

Dans le [Système Romme](https://fr.wikipedia.org/wiki/Calendrier_r%C3%A9publicain#Le_calendrier_r%C3%A9publicain_perp%C3%A9tuel), le 1<sup>er</sup> Vendémiaire, premier jour de l'an, correspond au 22 Septembre sur une période de l'an grégorien 1992 (an CCI) à 2091 (an CCC).

Le calcul de la date se fait donc en comptant le nombre de jours écoulés depuis le dernier 22 Septembre.

La liste des noms de jours est extraite de [Wikipédia](https://fr.wikipedia.org/wiki/Calendrier_r%C3%A9publicain#Exemple_de_calendrier_r%C3%A9publicain)
