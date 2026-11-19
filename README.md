# Liste de mots de Lettern (français)

Ce dépôt contient les listes de mots et les données des grilles du livre français de **Lettern**,
un jeu de mots tranquille pour iPhone de Tickwork, publiées sous licence
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr).

État au 2026-11-19 · listes `fr-2026-11-18+sha256:76ce57c11bf7` · Lettern 1.2.0 ·
le livre allemand : <https://github.com/inesgolubapps/lettern-wortliste>

Dans Lettern, tu fais glisser ton doigt sur une roue de lettres pour former des mots et remplir
une petite grille de mots croisés. Les mots qu’une grille demande, et ceux qu’elle accepte comme
mots bonus, se trouvent dans ce dépôt, avec chaque page du livre et chaque grille du jour. Les
données sont tirées de sources ouvertes, notamment Lexique, le Wiktionnaire et wordfreq, et sont
donc, comme elles, sous CC BY-SA 4.0.

## Contenu

| Fichier | Contenu | Taille |
| --- | --- | --- |
| `data/ziel.tsv` | vocabulaire cible : les mots qu’une grille peut demander, avec leur orthographe, leur forme de base, leur catégorie et leur fréquence | 9,764 formes en 12,581 lignes |
| `data/bonus.tsv` | mots acceptés : toute forme qui compte comme mot bonus, avec son orthographe | 587,880 formes |
| `data/levels.json` | le livre : chaque page avec ses galets, sa grille, ses mots cibles et ses mots bonus | 640 pages en 40 chapitres |
| `data/daily.json` | les grilles du jour, au même format | 420 grilles |
| `curation/decisions.tsv` | journal de la relecture mot par mot : une ligne par décision, avec sa raison | 11,306 lignes |
| `curation/never-target.txt` | mots valides jamais demandés, avec la raison | |
| `curation/always-target.txt` | mots demandés bien qu’une règle les écarterait | |
| `SOURCES.md` | chaque source avec sa version, sa somme de contrôle et sa licence | |
| `FORMAT.md` | les colonnes et champs de chaque fichier | |
| `LICENSE` | le texte juridique de la CC BY-SA 4.0 | |
| `VERSION`, `SHA256SUMS` | état et sommes de contrôle de chaque fichier | |

Les noms `ziel.tsv` (« cible » en allemand) et les noms de colonnes reprennent ceux du dépôt
allemand, pour que les mêmes outils lisent les deux.

## Galets et orthographe

Les galets de la roue et les cases de la grille ne portent **pas d’accents** : É, È, Ê, Ë et E sont
le même galet, Ç est un C, Œ s’écrit OE. La colonne `form` contient donc la forme sans accents
(`ecole`), la colonne `show` l’orthographe correcte (`école`), que l’app montre sur la feuille
« Résolu. », dans la liste des mots bonus et quand on consulte un mot. Quand plusieurs orthographes
donnent la même forme (*pêche*, *péché*, *pèche* → `peche`), la forme compte une fois et `show` donne
l’orthographe retenue pour l’affichage : en général la plus fréquente, avec quelques priorités de
curation (ligature *œ*, *thé* plutôt que *the*).

## Quels mots comptent

- **Mots cibles** : des mots que l’on connaît au quotidien, en France, en Belgique, en Suisse et au
  Québec, sous leur forme de base ou une forme courante (*jours*, *mangé*). Seuls eux sont demandés.
  Les régionalismes (*septante*, *nonante*), les mots rares, familiers ou sensibles n’en font pas
  partie.
- **Mots bonus** : d’autres mots français attestés dans le Wiktionnaire ou le Wiktionary, formes
  fléchies et régionalismes compris (3 à 10 lettres, sans apostrophe ni trait d’union, hors liste de
  filtrage), et les deux orthographes de la réforme de 1990 (*oignon* et *ognon*). Ils
  sont acceptés, jamais demandés.
- Les noms propres, les abréviations, les insultes et les mots les plus grossiers, les mots avec apostrophe, trait d’union ou espace
  (*aujourd’hui*, *peut-être*) et les mots de moins de trois lettres ne comptent pas. Les listes
  contiennent des mots de 3 à 10 lettres.

## Attribution

Les données sont tirées de ces œuvres. Fichiers, versions et sommes de contrôle : [SOURCES.md](SOURCES.md).

1. **Lexique 4** – Boris New, Christophe Pallier et al., <http://www.lexique.org>. Licence :
   CC BY-SA 4.0.
2. **Wiktionnaire** – les contributrices et contributeurs du Wiktionnaire,
   <https://fr.wiktionary.org>, rendu lisible par machine par kaikki.org avec wiktextract
   (Tatu Ylonen), <https://kaikki.org/frwiktionary/>. Licence : CC BY-SA 4.0 (aussi GFDL ; nous
   utilisons la CC BY-SA 4.0).
3. **Wiktionary, édition anglaise, entrées françaises** – les contributrices et contributeurs du
   Wiktionary anglais, <https://en.wiktionary.org>, via kaikki.org/wiktextract. Licence :
   CC BY-SA 4.0 (aussi GFDL).
4. **wordfreq** – Robyn Speer, <https://github.com/rspeer/wordfreq>. Licence des données :
   CC BY-SA 4.0. Les fréquences françaises comprennent des sous-titres du projet **OpenSubtitles**
   (<http://www.opensubtitles.org/>) via OPUS et le **Google Books Ngram Viewer**
   (<https://books.google.com/ngrams>), en plus de Wikipédia, de la presse, du web, de Twitter et de
   Reddit.

Ces œuvres sont fournies par leurs auteurs en l’état ; la clause de non-responsabilité de leur
licence s’applique (pour la CC BY-SA 4.0, section 5, voir [LICENSE](LICENSE)).

## Ce que nous avons changé

Les fichiers ne sont pas des copies des sources, mais en sont tirés (adaptation au sens de la
section 3(a)(1)(B) de la licence) :

- **Extrait.** De Lexique les formes, lemmes, catégories, fréquences et le degré de familiarité ; du
  Wiktionnaire et du Wiktionary seulement les entrées de langue française : mot, catégorie, formes
  et marques d’usage (vulgaire, vieilli, régional …). Aucune définition.
- **Filtré.** Retirés : noms propres, abréviations, formes avec apostrophe, trait d’union ou espace,
  orthographes d’avant 1835, insultes et mots les plus grossiers (voir « Non inclus »). D’autres mots
  familiers, vulgaires ou sexuels restent des mots bonus valides, mais ne sont jamais demandés.
- **Fusionné.** Les accents sont retirés pour la forme des galets ; la fréquence de chaque forme
  (colonne `zipf`) vient de wordfreq.
- **Sélectionné par fréquence et familiarité.** Les mots cibles ont un sens neutre et non régional,
  dépassent un seuil de fréquence, et la plus rare des deux orthographes d’une paire de la réforme de
  1990 n’est jamais demandée.
- **Relu.** Les formes cibles ont été relues mot par mot ; ce qui a été retiré, ajouté ou corrigé est
  dans `curation/`, avec la raison.
- **Grilles générées.** `levels.json` et `daily.json` ont été générés à partir des listes par
  notre propre programme ; chaque page est vérifiée automatiquement. À partir du chapitre 3, les
  mots-clés viennent de nos propres listes thématiques.

## Licence

Les données de ce dépôt sont sous **Creative Commons Attribution – Partage dans les mêmes conditions
4.0 International (CC BY-SA 4.0)** : <https://creativecommons.org/licenses/by-sa/4.0/deed.fr>. Le texte
juridique complet est dans [LICENSE](LICENSE) (récupéré le 2026-10-01 sur
<https://creativecommons.org/licenses/by-sa/4.0/legalcode.txt>).

Tu peux copier, modifier et partager les données, aussi à des fins commerciales, à condition de
créditer les auteurs, d’indiquer tes modifications et de partager ta version sous la même licence ou
une licence compatible.

## Réutilisation

Cette ligne crédite tous les auteurs et peut être copiée telle quelle :

```
« Liste de mots de Lettern » par Tickwork, état au 2026-11-19, https://github.com/inesgolubapps/lettern-wordlist-fr, sous licence CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Tirée de Lexique 4 (Boris New, Christophe Pallier et al.), du Wiktionnaire et du Wiktionary (leurs contributrices et contributeurs, via kaikki.org/wiktextract) et des données de wordfreq (Robyn Speer), toutes trois sous CC BY-SA 4.0 ; wordfreq intègre des données d’OpenSubtitles et du Google Books Ngram Viewer.
```

## Signaler une erreur

Un mot manque, est mal orthographié ou n’a pas sa place dans un jeu ? Dis-le-nous :

- en ouvrant un ticket dans ce dépôt : <https://github.com/inesgolubapps/lettern-wordlist-fr/issues>
- dans l’app : après « Résolu. », touche le mot et signale-le
- par e-mail à inesgolubapps@gmail.com

## Non inclus

- **Le code.** Le code de l’app et les outils qui construisent ces fichiers ne font pas partie de ce
  dépôt et ne sont pas couverts par la licence.
- **La liste de filtrage.** À la construction, une liste séparée écarte les insultes et les mots les
  plus grossiers, à partir du Wiktionnaire et de nos propres listes (une liste publique de mots
  grossiers sert seulement d’aide à la relecture, voir SOURCES.md). Elle n’est publiée ni ici ni avec
  l’app ; aucun de ses mots ne figure dans un fichier de ce dépôt. Pour la même raison, `curation/decisions.tsv` omet les 44 lignes qui
  la concernent.
- Le nom, les images, les sons, les polices et les textes de l’app.

## Aucune garantie

Les données ont été réunies pour un jeu, pas comme dictionnaire ni comme aide à l’orthographe. Elles
sont fournies en l’état, sans garantie d’exactitude ni d’exhaustivité. La responsabilité liée à leur
usage est exclue dans la mesure permise par la loi (section 5 de la licence).
