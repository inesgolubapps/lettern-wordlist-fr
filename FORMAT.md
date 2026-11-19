# Formats des fichiers

État au 2026-11-19 · listes `fr-2026-11-18+sha256:76ce57c11bf7`

Tous les fichiers sont en UTF-8, forme normale Unicode NFC, fins de ligne LF. Les fichiers TSV ont
une ligne d’en-tête et séparent les colonnes par une tabulation ; pas de guillemets, pas
d’échappements. Les nombres décimaux utilisent un point.

**Formes** (`form`, `lemma`, `w`, `leit`, `bonus`) : en minuscules, lettres a–z uniquement, **sans
accents** (é → e, ç → c, œ → oe), exactement comme les galets de la roue. Une forme des listes a 3 à
10 lettres. L’orthographe correcte est dans `show`.

Les noms de fichiers et de colonnes viennent du dépôt allemand (`ziel` = cible, `entscheidung` =
décision, `grund` = raison), pour que les mêmes outils lisent les deux.

## data/ziel.tsv — vocabulaire cible

Les mots qu’une grille peut demander. Une ligne par **sens associé à un lemme** : une forme qui appartient à plusieurs
lemmes apparaît plusieurs fois. La première ligne d’une forme est l’analyse la plus probable. Lignes
triées par `form`.

| Colonne | Contenu | Exemple |
| --- | --- | --- |
| `form` | la forme, sans accents | `foret` |
| `show` | l’orthographe correcte, la même dans toutes les lignes d’une forme | `forêt` |
| `lemma` | lemme de cette analyse, sans accents | `foret` |
| `pos` | catégorie : `noun`, `verb`, `adj`, `adv`, `pron`, `prep`, `conj`, `num`, `other` (articles, déterminants) | `noun` |
| `zipf` | fréquence de la forme sur l’échelle de Zipf, deux décimales ; la même dans chaque ligne d’une forme | `4.61` |

- **Zipf** est le logarithme décimal du nombre d’occurrences par milliard de mots : 3 ≈ une fois par
  million de mots, 6 une fois par mille. Les valeurs viennent de wordfreq (voir SOURCES.md) ; pour les
  homographes d’un nom propre (*pierre*/Pierre), la valeur vient des sous-titres de Lexique, plus bas.
- Des lemmes qui ne diffèrent que par les accents (*pêche*, *péché*) ont le même `lemma` : une grille
  ne demande jamais les deux.
- Une grille demande au plus une forme par lemme.

9,764 formes en 12,581 lignes ; les premières lectures appartiennent à
6,160 lemmes.

## data/bonus.tsv — mots acceptés

Chaque forme que le jeu accepte, avec son orthographe. Chaque forme de `ziel.tsv` y est aussi. Triées
par `form`.

| Colonne | Contenu | Exemple |
| --- | --- | --- |
| `form` | la forme, sans accents | `coeur` |
| `show` | l’orthographe retenue pour l’affichage, en général la plus fréquente de celles qui donnent cette forme | `cœur` |

```
coeur	cœur
ete	été
peche	pêche
```

- Les deux orthographes de la réforme de 1990 sont acceptées (*oignon*, *ognon*) ; une seule peut être
  demandée.
- Les régionalismes (*septante*, *nonante*) sont acceptés, jamais demandés.

587,880 formes.

## data/levels.json, data/daily.json — grilles

Les deux fichiers ont le même format : un objet JSON contenant un tableau `pages` (chaque page est écrite sur sa propre ligne).

| Champ | Contenu |
| --- | --- |
| `v` | version du format, actuellement `1` |
| `lang` | langue du livre, `fr` |
| `lexicon` | état des listes avec lesquelles les grilles ont été générées et vérifiées (comme `lexicon` dans `VERSION`) : `fr-`, la date des sources et une partie d’une somme de contrôle sur les listes ; elle couvre aussi la liste de filtrage non publiée |
| `generator` | programme et version qui ont généré les grilles |
| `pages` | les pages |

### Une page

| Champ | Contenu |
| --- | --- |
| `page` | numéro de page, 1–640 dans le livre ; pour les grilles du jour, le numéro courant |
| `bogen` | chapitre 1–40, 16 pages chacun ; `0` pour les grilles du jour |
| `kind` | `kreuz` (mots croisés) ou `freisatz` (le sommet : mots sans croisements, en colonnes) |
| `theme` | seulement dans le livre à partir du chapitre 3 : le thème du chapitre comme identifiant interne, p. ex. `garten` (les identifiants sont allemands ; l’app affiche un nom français) |
| `leit` | mot-clé : le mot cible qui utilise tous les galets |
| `tiles` | les galets de la roue dans leur position de départ, dans le sens des aiguilles d’une montre depuis le haut : majuscules `A`–`Z`, sans accents |
| `cols`, `rows` | seulement pour `kreuz` : largeur et hauteur de la grille en cases |
| `words` | les mots cibles, voir ci-dessous |
| `bonus` | les mots bonus : chaque forme de la liste acceptée que l’on peut former avec les galets et qui n’est pas un mot cible de la page ; complet et trié |
| `bonusShow` | l’orthographe de chaque mot bonus, à la même position que dans `bonus` |
| `difficulty` | mesure de difficulté entre 0 et 1 ; sert seulement à l’ordre |
| `seed` | valeur de départ du générateur (hexadécimal) |

Un mot cible dans `words` :

| Champ | Contenu |
| --- | --- |
| `w` | la forme, sans accents |
| `show` | l’orthographe, comme la montrent la feuille « Résolu. » et la liste des mots ; la grille montre les galets sans accents |
| `r`, `c` | seulement pour `kreuz` : ligne et colonne de la première lettre, comptées à partir de 0 en haut à gauche |
| `d` | seulement pour `kreuz` : direction, `H` horizontal vers la droite, `V` vertical vers le bas |

### Le livre (levels.json)

640 pages en 40 chapitres de 16 pages ; la dernière page de chaque chapitre est un
`freisatz`. 5,967 mots cibles et 61,575 mots bonus.

### Les grilles du jour (daily.json)

420 grilles. La grille numéro *n* appartient au jour 28 septembre 2026 plus *n* − 1 jours ;
après la dernière, la suite recommence. 3,465 mots cibles et 31,222 mots bonus.

## curation/decisions.tsv — journal de relecture

Une ligne par décision sur une forme, avec sa raison. Le journal n’agit pas sur les listes ; les listes
manuelles ci-dessous, si. Si une forme apparaît plusieurs fois, la ligne au `pass` le plus élevé compte.

| Colonne | Contenu |
| --- | --- |
| `form` | la forme |
| `entscheidung` | décision : `ok` reste cible (aussi : orthographe affichée corrigée, voir la raison) · `ziel-nein` mot bonus valide, jamais cible · `ziel-pflicht` devient cible |
| `grund` | raison, en quelques mots (en allemand) |
| `pass` | passe de relecture, `1`, `2`, … |

Les 44 lignes qui concernent la liste de filtrage ne sont pas publiées.

## curation/*.txt — listes manuelles

Une forme par ligne, en minuscules ; `#` commence un commentaire jusqu’à la fin de la ligne.

| Fichier | Format | Effet |
| --- | --- | --- |
| `never-target.txt` | `forme  # raison` | mot bonus valide, jamais cible |
| `always-target.txt` | `forme  # raison` | cible, à condition que la forme soit dans la liste acceptée |
| `reading-priority.txt` (si présent) | `forme  lemme[:catégorie]  # raison` | fixe la première analyse d’une forme dans `ziel.tsv` |

## VERSION et SHA256SUMS

`VERSION` indique, en lignes `clé: valeur`, l’état de ce dépôt (`date`), des listes (`lexicon`), des
sources (`sources`) et la version de l’app (`app`). `SHA256SUMS` contient la somme SHA-256 de chaque
fichier ; vérifier avec `shasum -a 256 -c SHA256SUMS` (macOS) ou `sha256sum -c SHA256SUMS` (Linux).
