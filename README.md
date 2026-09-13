# Cahier du Labo

Suivi du stock de pâtisseries et plan de production quotidien, pour la
boulangerie. Une page, aucun compte à créer : chaque personne entre son
code et saisit ce qu'elle produit et ce qui sort.

## Mise en service

1. `config.js` reçoit les identifiants du projet Firebase. Tant qu'il est
   vide, l'appli tourne en local : chaque appareil garde ses propres
   saisies, rien n'est partagé.
2. Publier le dossier sur GitHub Pages.
3. Sur un téléphone, ouvrir le lien puis « Ajouter à l'écran d'accueil ».

## Données

Trois collections Firestore :

- `acces` — une personne par document : `nom`, `code`, `role`
  (`direction` ou `labo`), `ordre`.
- `produits` — une référence par document : `nom`, `seuil`, `ordre`,
  `type` (`p` produite au labo, `a` achetée), `base` (identifiant de la
  matière consommée, vide la plupart du temps).
- `jours` — un document par date, `e` contenant une ligne par saisie :
  `p` la référence, `t` le type (`p` entrée, `s` sortie, `a` correction),
  `q` la quantité, `h` l'heure, `u` le prénom.

Chaque saisie porte un identifiant unique et s'écrit en fusion : deux
personnes qui saisissent la même référence au même moment ne peuvent pas
s'effacer.
