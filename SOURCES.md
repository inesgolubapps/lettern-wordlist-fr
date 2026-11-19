# Sources

Sources au 2026-11-18 · listes `fr-2026-11-18+sha256:76ce57c11bf7`

Chaque source est épinglée à exactement un fichier : adresse, version et somme de contrôle SHA-256.
Les fournisseurs reconstruisent régulièrement leurs fichiers (kaikki.org chaque semaine, lexique.org
de temps en temps) et ne gardent pas les anciens états ; la même adresse sert donc souvent aujourd’hui
un fichier plus récent avec une autre somme de contrôle. L’état du Wiktionnaire peut être reconstruit
avec wiktextract à partir des dumps Wikimedia des jours indiqués.

Toutes les œuvres sont fournies par leurs auteurs en l’état ; la clause de non-responsabilité de la
licence respective s’applique.

## Dans les données

### 1. Lexique 4.10

| | |
| --- | --- |
| Auteurs | Boris New, Christophe Pallier, Gauvain Schalchli, Jessica Bourgin, Manuel Gimenes et al., <http://www.lexique.org> |
| Fichier | `Lexique410.zip` |
| Adresse | <https://www.lexique.org/databases/Lexique/Lexique410.zip> |
| Version | Lexique 4.10, archive du 2026-11-17 |
| SHA-256 | `f85ce56620a6822a425556f5feffb0da134c21d8349dd89f0d8e0bc0d7404d54` |
| Licence | CC BY-SA 4.0 (« Lexique est distribuée sous une licence CC BY-SA 4.0 », lexique.org) |
| Usage | lemmes et catégories (une forme par lemme et par page), fréquence dans les sous-titres, degré de familiarité des mots, choix des mots cibles |

Référence demandée par les auteurs : New, B., Pallier, C., Schalchli, G., Bourgin, J. & Gimenes, M.
(2026). Lexique 4: a major upgrade of the « Lexique » French Lexical Database. *Behavior Research
Methods*.

### 2. Wiktionnaire (Wiktionary en français)

| | |
| --- | --- |
| Auteurs | les contributrices et contributeurs du Wiktionnaire, <https://fr.wiktionary.org>; extraction kaikki.org / wiktextract (Tatu Ylonen) |
| Fichier | `kaikki.org-dictionary-Français.jsonl` (entrées de langue française) |
| Adresse | <https://kaikki.org/frwiktionary/Fran%C3%A7ais/kaikki.org-dictionary-Fran%C3%A7ais.jsonl> |
| Version | dump frwiktionary du 2026-10-01, extrait le 2026-11-02 (wiktextract 19f9a30 / 6f96ddf) |
| SHA-256 | `80f83adccc1563c14e10d509bdc32eb56b7ed310512ca73416c1f0bda8be4d85` |
| Licence | CC BY-SA 4.0 (aussi GFDL ; nous utilisons la CC BY-SA 4.0) |
| Usage | existence des mots (mots acceptés), formes fléchies, marques d’usage (vulgaire, vieilli, régional …), orthographe rectifiée de 1990, noms propres |

### 3. Wiktionary, édition anglaise, entrées françaises

| | |
| --- | --- |
| Auteurs | les contributrices et contributeurs du Wiktionary anglais, <https://en.wiktionary.org>; extraction kaikki.org / wiktextract (Tatu Ylonen) |
| Fichier | `kaikki.org-dictionary-French.jsonl.gz` |
| Adresse | <https://kaikki.org/dictionary/French/kaikki.org-dictionary-French.jsonl.gz> |
| Version | dump enwiktionary du 2026-10-01, extrait le 2026-10-30 (wiktextract 19f9a30 / 6f96ddf) |
| SHA-256 | `224fce45865bad43c4f43f11d0f6fc84e044ffda8407c549609639cfc7d38cc7` |
| Licence | CC BY-SA 4.0 (aussi GFDL ; nous utilisons la CC BY-SA 4.0) |
| Usage | second avis : existence, conjugaisons, marques d’usage |

### 4. wordfreq

| | |
| --- | --- |
| Auteur | Robyn Speer, <https://github.com/rspeer/wordfreq> |
| Paquet | wordfreq 3.1.1 (PyPI), SHA-256 du fichier .whl `4b1c6ecffc6198be3396d5cf871c4423ca71c907c231348d352dd54d62b97473` |
| Fichier de données | `wordfreq/data/large_fr.msgpack.gz`, SHA-256 `6f16cd80b9b66c5698ed002becea83ae30d0584c3205f1cf01714ad562c00c8b` |
| Licence | données CC BY-SA 4.0, code Apache 2.0 |
| Contenu pour le français | Wikipédia, sous-titres (OpenSubtitles via OPUS), presse, livres (Google Books Ngram Viewer, <https://books.google.com/ngrams>), web, Twitter, Reddit |
| Usage | fréquence de chaque forme (colonne `zipf`), choix de l’orthographe affichée quand plusieurs se confondent |

## Seulement à la construction (non publié)

### 5. List of Dirty, Naughty, Obscene, and Otherwise Bad Words (LDNOOBW), fr

| | |
| --- | --- |
| Adresse | <https://raw.githubusercontent.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words/5faf2ba42d7b1c0977169ec3611df25a3c08eb13/fr> |
| Version | git 5faf2ba (2020-07-13) |
| SHA-256 | `79763a705e08256b393952852bb63aa903f4485e0ef02f70735f5e50efff213c` |
| Licence | CC BY 4.0 |
| Usage | uniquement pour signaler des mots à relire ; aucun mot n’est retiré à cause d’elle seule. La liste de filtrage n’est pas publiée (README, « Non inclus ») |

## Non utilisé

Grammalecte/Dicollecte et les dictionnaires Hunspell français (MPL 2.0, GPL, LGPL) ne sont utilisés
ni comme source ni comme filtre ; aucune liste officielle de Scrabble (ODS).
