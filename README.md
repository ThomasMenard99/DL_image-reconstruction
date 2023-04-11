# ProjetDL

### Résumé du projet

Le but du projet est de reconstruire une image comportant un masque blanc en son centre.

Pour cela nous nous basons sur un article de 2016 - Context encoders : feature learning by inpainting. Cet article utilise des context encoders pour générer la partie manquante de l'image.

### Base de données
Nous utilisons la base de données celebA, disponible ici : https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html.
Nous entrainons notre modèle sur 80 000 images (sur une base originale comportant 200 000 images, par soucis de temps d'entraînement).
Notre validation dataset comprend 2 000 images de la même base de données. 
Enfin, notre dataset de test comprend les visages des étudiants de la classe (environ 30 images).

Avant de lancer le code de notre projet, il faut donc télécharger le dataset celebA. Le téléchargement et dézippage de l'information peut prendre plusieurs heures en raison de la taille de la base de données.

### Modèle

##### Architecture
Notre modèle de context encoder comprend un encodeur qui transforme l'image en un vecteur latent de dimension (4000 x6 x6). Ensuite, nous utilisons un décodeur qui utilise ce vecteur latent pour créer le masque manquant à l'image. L'ensemble formé par l'encodeur et le décodeur constitue donc le générateur d'images.
Le discriminateur utilisé par la suite permet d'améliorer les images générées, en détectant si elles sont réelles ou virtuelles (donc créées par le générateur).
Dans la structure dite Adversarial GAN, le générateur et le discriminateur s'améliorent mutuellement en tentant de se tromper l'un l'autre. C'est cette architecture qui permet à notre réseau de reconstituer une grande partie de l'image.

##### Fonctions de coût
Nous utilisons deux fonctions coûts différentes afin d'obtenir un meilleur résultat.
La première fonction de cout est la MSE loss (pour obtenir des images plus proches de la réalité), la seconde est la L1 loss (afin d'obtenir le contexte général de l'image). La pondération entre ces deux loss est issue des données de l'article de Pathak et al, et de 99,9% d'importance pour la L1 loss contre 0,01% pour la MSE loss.

### Résultats
![Alt text](https://github.com/ThomasMenard99/Image-reconstruction/blob/main/85007.png?raw=true "Results")
