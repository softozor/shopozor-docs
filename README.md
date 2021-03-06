# Documentation du shopozor

Ce dépôt sert de documentation pour le projet de shopozor. Le langage utilisé
est le RestructuredText avec les extensions propres à Sphinx.

La documentation est publiée sur http://docs.shopozor.surge.sh/ ou http://dev.docs.shopozor.surge.sh/ (version développeurs).

## Prérequis sur Ubuntu

Il faut installer pipenv

```bash
sudo pip3 install pipenv
```

## Étapes à suivre

Cloner le dépôt

```bash
git clone git@github.com:softozor/shopozor-docs.git
cd shopozor-docs
# initialisation de l'environnement virutel
pipenv shell
# installation des dépendances (Sphinx etc ...)
pipenv install
```

## Commandes propres à Sphinx

Pour lancer la compilation du projet et publier les modifications, il y a plusieurs "commandes" dans le `Makefile`.

### Mode développement

Lorsque l'on crée des modifications sur la documentation, on peut lancer la commande 

```
make livehtml
```

dans la racine du dossier (celui où se trouve le fichier `Makefile`) et cela va lancer un serveur de développement qui dispose du LiveReload : dès qu'un fichier `.rst` est modifié, la projet est recompilé et le site mis à jour dans le navigateur.

L'adresse pour visualiser le résultat est http://localhost:8080/

### Résolution de problèmes

Il arrive que Sphinx ne voit pas les changements effectués dans les fichiers `.rst`. Il faut à ce moment quitter la commande `make livehtml` avec Ctrl + C et faire 

```
make clean
make html
make livehtml
```

### Publication dans d'autres formats (LaTeX / PDF / etc ...)

ll existe d'autres formats cibles que le HTML. Voir le fichier Makefile, par exemple

```
make latex
make latexpdf
```

### Publication de la documentation sur surge.sh

Pour publier la documentation sur surge.sh, il faut installer `surge.sh` avec 

```
yarn global add surge
```

et s'identifier avec 

```
surge login
```

Ensuite, on peut faire 

```
make deploy
```

Il faut pour cela avoir les autorisations pour publier sur le site  http://docs.shopozor.surge.sh/ et  http://dev.docs.shopozor.surge.sh/. L'utilisateur pour ces sites est cedonner 'at' gmail.com.

## Ressources pour l'utiisation de Sphinx

Sphinx est le système de documentation utilisé par la communauté Python et est vraiment très puissant, notamment pour documenter du code source. Il dispose également d'un très grand nombre d'extensions permettant notamment d'intégrer des diagrammes UML directement dans la documentation.

*   Page d'accueil du projet Sphinx : http://www.sphinx-doc.org/en/master/
*   Gettings Started : http://www.sphinx-doc.org/en/master/usage/quickstart.html#defining-document-structure
*   Référence du langage RestructuredText (dialecte Sphinx) : http://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html
    *   Documentation officielle du langage RestructuredText : http://docutils.sourceforge.net/rst.html

