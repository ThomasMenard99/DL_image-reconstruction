# ProjetDL

### Résumé du projet

Le but du projet est de reconstruire une image comportant un masque blanc

Pour cela nous nous basons sur un article de 2016 - Context encoders : feature learning by inpainting. Cet article utilise des context encoders pour générer la partie manquante de l'image.

### Base de données
Nous utilisons la base de données celebA, disponible ici : https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html.
Nous entrainons notre modèle sur 80 000 images.
Notre validation dataset comprend 2 000 images de la même base de données. 
Enfin, notre dataset de test comprend les visages des étudiants de la classe (environ 30 images).


### Modèle

##### Architecture
Notre modèle comprend un encodeur qui transforme l'image en un vecteur latent de dimension (4000 x6x6). Ensuite, nous utilions un décodeur qui utilise ce vecteur latent pour créer le masque manquant à l'image.
Le discriminateur utilisé par la suite permet d'améliorer les images générées.

##### Fonctions de couts
Nous utilisons deux fonctions couts différentes afin d'obtenir de meilleur résultat.
La première fonction de cout est la MSE loss (pour obtenir ds images plus proches de la réalité), la seconde est la L1loss (afin d'obtenir le contexte générale de l'image).

### Résultats
![Alt text](https://github.com/ThomasMenard99/Image-reconstruction/blob/main/85007.png?raw=true "Title")
