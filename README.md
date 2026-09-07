# Mémoire de M2 TNAH — Clara Martin

*À demeure, en partage, conservation in situ et diffusion en réseau des archives historiques d’une institution universitaire. Le cas de la Faculté de médecine de l’Université de Montpellier.*

Mémoire réalisé dans le cadre du Master 2 Technologies numériques appliquées à l'histoire (École nationale des chartes – PSL), année universitaire 2025-2026.

## Contenu du dépôt

Le dépôt contient les fichiers nécessaires à la consultation et à la compilation du mémoire :

- `memoire.tex` : document maître ;
- `chapitres/` : fichiers `.tex` constituant le mémoire :
  - `page-titre.tex`
  - `resume.tex`
  - `remerciements.tex`
  - `introduction.tex`
  - `partie1.tex`
  - `partie2.tex`
  - `partie3.tex`
  - `conclusion.tex`
  - `bibliographie.tex`
  - `glossaire.tex`
  - `annexes.tex`
- `bibliographie.bib` : base bibliographique ;
- `enc.bbx` et `enc.cbx` : fichiers du style bibliographique utilisé ;
- `images/` : illustrations, graphiques, schémas et documents reproduits dans le mémoire ;
- `M2TNAH_2026_MARTIN_clara.pdf` : version finale compilée du mémoire.

Les fichiers auxiliaires produits automatiquement lors de la compilation (`.aux`, `.bbl`, `.bcf`, `.blg`, `.log`, `.out`, `.toc`, fichiers de glossaire, etc.) ne sont pas versionnés.

## Compilation

Le document est compilé avec XeLaTeX. La bibliographie est traitée avec Biber et les glossaires avec `makeglossaries`.

Ordre de compilation :

```bash
xelatex -interaction=nonstopmode memoire.tex
biber memoire
makeglossaries memoire
xelatex -interaction=nonstopmode memoire.tex
xelatex -interaction=nonstopmode memoire.tex
```

Une passe supplémentaire de XeLaTeX peut être nécessaire lors d'une première compilation complète pour stabiliser la pagination et les références.

Le style bibliographique `enc`, nécessaire à la compilation, est fourni directement dans le dépôt (`enc.bbx` et `enc.cbx`).

La compilation a été testée à partir d'un nouveau clone du dépôt. Après stabilisation, elle aboutit sans erreur, sans référence ou citation indéfinie et sans demande de nouvelle passe de XeLaTeX ou de Biber.

## Appropriation personnelle de LaTeX

À partir du document maître fourni dans le cadre du cours, j'ai adapté la mise en forme aux besoins particuliers du mémoire. Les principaux choix sont également expliqués dans les commentaires de `memoire.tex`.

J'ai notamment utilisé :

- plusieurs outils pour les tableaux (`tabularx`, `array`, `booktabs` et `longtable`), selon leur taille et leur contenu ;
- `rotating` et `pdflscape` pour les tableaux et figures en orientation paysage. Certains éléments sont volontairement tournés différemment selon leur place dans le volume, afin que leur haut soit orienté vers l'extérieur lors d'une impression recto-verso ;
- TikZ pour réaliser directement en LaTeX le graphe de modélisation CIDOC CRM présenté en annexe, avec des styles différents pour les types de nœuds et les relations ;
- `fancyhdr` pour personnaliser les en-têtes et les pieds de page et distinguer les pages paires et impaires ;
- les commandes personnelles `\chapitrecourt` et `\sectioncourte` pour donner une version abrégée de certains titres dans les en-têtes, sans modifier le titre complet dans le texte ou dans la table des matières ;
- `cleveref`, en complément de `hyperref`, pour faciliter et uniformiser les renvois internes. Ce package n'avait pas été abordé dans le cours.

Ces adaptations m'ont surtout permis de gérer les nombreux tableaux, schémas, annexes et renvois du mémoire, ainsi que sa consultation à l'écran et son impression.

### Documentation consultée

Pour ces adaptations, je me suis notamment appuyée sur la documentation des packages utilisés :

- `tabularx` : https://ctan.org/pkg/tabularx
- `rotating` : https://ctan.org/pkg/rotating
- `pdflscape` : https://ctan.org/pkg/pdflscape
- PGF/TikZ : https://pgf-tikz.github.io/pgf/pgfmanual.pdf
- `fancyhdr` : https://ctan.org/pkg/fancyhdr
- `cleveref` : https://ctan.org/pkg/cleveref

## Avertissements de mise en page

La compilation peut encore produire certains avertissements (`warnings`). Ils ne correspondent pas à des erreurs de compilation et ont été vérifiés dans le PDF final. Certains ont été conservés pour éviter de modifier une mise en page déjà satisfaisante.

Il s'agit notamment :

- de `Float too large for page` pour quelques figures et tableaux légèrement plus grands que l'espace normalement disponible. Leur taille a été conservée pour garder les éléments lisibles, notamment en orientation paysage ;
- d'avertissements de `fancyhdr` concernant la hauteur des en-têtes. Les en-têtes s'affichant correctement, je n'ai pas modifié globalement `\headheight`, ce qui aurait également modifié la mise en page et la pagination ;
- de `Overfull \hbox` et `Underfull \hbox`, principalement dans des passages où LaTeX dispose de peu de possibilités pour ajuster les lignes (URL, références bibliographiques, tableaux, légendes, etc.). Ils ont été conservés lorsqu'aucun problème visuel important n'apparaissait dans le PDF ;
- d'avertissements de `hyperref` (`Token not allowed in a PDF string`), liés à certaines commandes LaTeX présentes dans les titres et à leur conversion pour les signets du PDF. Ils n'affectent pas le texte affiché dans le document ;
- de quelques avertissements `biblatex` de type `Nested notes`, liés à des citations placées dans des notes déjà imbriquées. Ils n'empêchent pas la résolution des références bibliographiques.

La version finale a été compilée jusqu'à stabilisation de la pagination, des références croisées et de la bibliographie.
