## Nostalgie : Journal de bord

[TOC]  

===  

### 1.  Introduction  
Notre projet porte sur la recherche sur Internet du mot-clé "nostalgie" dans quatre langues : le portugais, le français, l'anglais et le chinois. Mon apport concerne principalement la fouille des liens chinois et anglais, autour des mots **乡愁 xiāngchóu** et **nostalgia**. les traitements de textes qui suivent, y compris l'extraction des mots vides, la génération des nuages de mots ainsi que l'analyse sur le portail iTrameur.  


### 2.  Préparation du corpus et du site HTML  

26/10 : Mise à jour de README.md sur le dépôt du groupe.  

09/11 : Regrouper 50 liens chinois dans un fichier.  

17/12 : Regrouper 50 liens anglais dans un fichier.  

21/12 : Vu que certains liens chinois ne fonctionnent pas correctement après l'éxécution du script bash, j'ai rajouté 22 liens de plus.  

23/12 : Premier essai de génération des nuages de mots  

-   Installation du module **wordcloud** pour générer les nuages de mots anglais et chinois avec la commdande wordcloud_cli dans le Terminal.  

-   Par contre, le rendu n'est pas satisfaisant à défaut d'exclure les mots vides pour les deux langues, de segmenter les phrases chinoises et de choisir une fonte propre au rendu des caractères chinois. Ainsi, j'ai décidé de me retourner vers Python pour préparer les textes et générer les nuages de mots de manière plus soigneuse.  
  
30/12 : ajout du contenu dans "A propos de nous", amélioration du script HTML

### 3.  Traitement de données

03/01 - 07/01 :  

-   Installation du module **jieba** pour faire la segmentation du chinois à partir du fichier "contexte" dans l'éditeur VS Code. Rédaction du script Python avec Jupyter Notebook. Ajout du fichier segmenté sur Github.  
  
-   Téléchargement de *SourceHanSerif.ttc* qui est une fonte open-source destinée à la typographie du chinois
-   Rédaction et amélioration du script
-   Installation du module **NLTK** pour la filtration de mots vides de l'anglais
    -   Pour les tokens anglais, je n'ai choisi d'abord que les mots en lettres minuscules avec une longueur égale ou supérieure à 3, à l'aide d'une expression régulière *[a-z]{3,}*.
    -   En fonction des premiers rendus, j'ai rajouté manuellement des mots vides anglais s'affichant sur l'image dans un liste et regénérer le nuage en les prenant en compte (cf. la variable *new_sw* dans la définition du fonction *filtering_en(file)* dans le script).  
    -   Vu qu'il faut encore exclure manuellement de nombreux mots et qu'il y a des mots à la fois cruciaux et fréquents comme "time", "past", "feel" etc., j'ai modifié la variable *filtered_list* en assignant la longueur *len(w)>=4* pour déterminer davantage les tokens pris en compte après avoir exclu de l'ensemble les mots vides pré-définis.  
    -   Afin de n'utiliser que les mots les plus fréquents, j'ai calculé la fréquence de tous les tokens obtenus et ne choisir que les 100 plus fréquents à l'aide des fonctions *Counter()* et *most_common()*.  

-   Traitement du chinois pour la génération des nuages de mots
    -   Les étapes pour le chinois sont quasiment identiques à celles pour l'anglais, sauf qu'il me faut utiliser l'expression régulière *[\u4e00-\u9fa5]{2,}* pour n'identifier que les caractères chinois et ne choisir que les mots non monosyllabiques, ainsi que taper manuellement dans un fichier à part les mots vides à partir des premières versions de nuages.   
-   Téléchargement de deux images pour les nuages avec masque : photos de lune et de maison  

  
### 4.  Analyse et rédaction  
08/01 - 10/01 :  
-   Réalisation finale des nuages de mots 
-   Rédaction de l'analyse pour le nuage de mots chinois sur le site.  
-   Chargement sur iTrameur le fichier *contexte* segmenté du chinois. Néanmoins, la page reste toujours dans l'étape *calcul en cours* et n'arrive pas à afficher le cadre, même si j'ai segmenté encore le fichier *dump*, supprimé les caractères *<lt;* et *>gt;* et essayé de le charger pour remplacer le fichier *contexte*.  
-   Analyse iTrameur pour le chinois. Comme je n'arrive pas à utiliser les outils tels que ventilation, carte et concordance, je ne peux observer les cooccurrents du mot 乡愁 dans la section *Coocs* et les cliquer pour consulter de plus près leur contexte dans les phrases.  
-   Réalisation des captures d'écran. Rédaction de l'analyse sur notre site.
-   Amélioration du script HTML. Dépôt final des fichiers sur GitHub.