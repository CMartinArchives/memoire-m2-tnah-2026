# Mémoire de M2 TNAH — Clara Martin

*À demeure, en partage, conservation in situ et diffusion en réseau des archives historiques d’une institution universitaire. Le cas de la Faculté de médecine de l’Université de Montpellier.*

Mémoire réalisé dans le cadre du Master 2 Technologies numériques appliquées à l'histoire (École nationale des chartes – PSL), année universitaire 2025-2026.

## Contenu du dépôt

Le dépôt contient l'ensemble des fichiers nécessaires à la consultation et à la compilation du mémoire :

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

Le style bibliographique `enc`, nécessaire à la compilation, est fourni directement dans le dépôt (`enc.bbx` et `enc.cbx`) afin que le projet soit autonome.

La compilation finale aboutit sans erreur, sans référence ou citation indéfinie et sans demande de nouvelle passe de XeLaTeX ou de Biber.

## Appropriation personnelle de LaTeX

Au-delà de la structure du document maître fourni dans le cadre du cours, la mise en forme du mémoire a fait l'objet de plusieurs adaptations développées en fonction des besoins propres au document. Ces choix sont également documentés par des commentaires dans `memoire.tex`.

Ils comprennent notamment :

- la combinaison de plusieurs environnements de tableaux (`tabularx`, `array`, `booktabs` et `longtable`) afin d'adapter leur composition à la nature et à la longueur des données présentées ;
- une gestion spécifique des tableaux et figures en orientation paysage avec `rotating` et `pdflscape`. Pour la consultation imprimée en recto-verso, certains éléments sont volontairement orientés en fonction de leur position dans le volume afin que le haut du contenu soit tourné vers l'extérieur du livre ;
- la réalisation directe en LaTeX, avec TikZ, du graphe de modélisation CIDOC CRM présenté en annexe, avec définition de styles de nœuds et représentation des relations entre entités ;
- la personnalisation des en-têtes et pieds de page avec `fancyhdr`, en distinguant pages paires et impaires ;
- la création des commandes personnelles `\chapitrecourt` et `\sectioncourte`, qui permettent d'employer dans les en-têtes des versions abrégées des titres sans modifier les titres développés dans le corps du mémoire ni leurs entrées dans la table des matières ;
- l'utilisation de `cleveref`, en complément de `hyperref`, pour améliorer et harmoniser les renvois internes. Ce package constitue notamment un ajout par rapport aux éléments étudiés dans le cours.

Ces adaptations répondent aux contraintes particulières d'un mémoire comportant de nombreux tableaux, schémas, annexes et références croisées, et destiné à une consultation à la fois numérique et imprimée.

### Documentation consultée

- `tabularx` : https://ctan.org/pkg/tabularx
- `rotating` : https://ctan.org/pkg/rotating
- `pdflscape` : https://ctan.org/pkg/pdflscape
- PGF/TikZ : https://pgf-tikz.github.io/pgf/pgfmanual.pdf
- `fancyhdr` : https://ctan.org/pkg/fancyhdr
- `cleveref` : https://ctan.org/pkg/cleveref

## Avertissements de mise en page

Le journal de compilation peut néanmoins contenir certains avertissements (`warnings`) qui ne constituent pas des erreurs de compilation.

Plusieurs ont été conservés volontairement après vérification de la version PDF finale afin de ne pas altérer une mise en page choisie et stabilisée, notamment :

- des avertissements `Float too large for page` concernant certaines figures et certains tableaux dont les dimensions ont été volontairement maintenues afin de préserver leur lisibilité et leur composition, en particulier pour les éléments complexes ou présentés en orientation paysage ;
- des avertissements `fancyhdr` relatifs à la hauteur réservée aux en-têtes. La modification globale de `\headheight` aurait entraîné une modification de la géométrie et de la pagination du document ; les en-têtes étant correctement affichés dans la version finale, leur paramétrage a été conservé ;
- des avertissements `Overfull \hbox` et `Underfull \hbox`, principalement liés à des contenus peu flexibles (références bibliographiques, URL, tableaux, légendes ou autres éléments contraints). Ils ont été conservés lorsqu'ils n'entraînaient pas de défaut visuel problématique dans le PDF ;
- des avertissements de `hyperref` (`Token not allowed in a PDF string`) liés à la conversion de certaines commandes LaTeX présentes dans les titres en chaînes destinées aux signets PDF ; ils n'affectent pas la composition imprimée du document ;
- quelques avertissements `biblatex` de type `Nested notes`, liés à l'emploi de citations dans des contextes de notes imbriquées et sans incidence sur la résolution des références bibliographiques.

Ces avertissements ont donc été distingués des erreurs de compilation. La version finale a été compilée jusqu'à stabilisation complète des références croisées et de la bibliographie.
