
## Introduction


## Materiels



## Travail à faire

scenarios 
Soint les points Pi(0<i<N) de la Pallette, P0 le point de depart, pPrise position de prise, pPose la position de depose, pAvant,pApres les position respectivment 
avant et apres la prise de piece sur le convoyeurs, pa les positions d'approche, px les positions de depose de pieces sur la palette,
soient Dx,DY et DZ la distances entre les positions suivant respectivement les axes x,y et z

1. Apprendre des points Pi(0<i<N) des Pallettes A, B, C .
  Ecrire un programme correspondant au robot de prendre les pieces sur le convoyeur et les poser sur les pallette A
Deduire l'algorithme qui permet de faire la meme operation connaissant les points seulement les positions P0 et P1

![Pallete Jaune](./Imgs/J1.jpeg)
   
3. Ecrire le programme correspondant au robot de prendre les pieces sur le convoyeur et les poser sur la pallette sur deux niveaux
 Deduire l'algorithme qui permet de faire la meme operation connaissant les points seulement les positions P0 et P1

5.  Ecrire le programme correspondant au robot de prendre les pieces sur le convoyeur et les poser sur la pallette sur deux niveaux
 Deduire l'algorithme qui permet de faire la meme operation connaissant les points seulement les positions P0 et P1

7.  Deduire l'algorithme qui permet de faire la meme operation  connaissant les points seulement les positions P0 et P1 et les dimentions de la pallette NxMxH
8.  Les pieces arrivent sur le convoyeur, On souhaite disposer les pieces sur la palette A selon les couleurs et chaque niveau corrrespont à une couleur bien precise:
Jaune-vert-bleu
Bleu-Jaune-vert
Vert-bleu-jaune 
Pour ce faire, on dispose d'une base de données database.db. Lorsque la piece arrive au Point de Prise, la camera scanne l'arucode pour determiner son ID et sa couleur qui sont enregister sont publiés comme de topic ROS2. Le PC s'abonne au topic couleur et l'enregistre dans la base de données. Vous utilierez la database.db pour construire vos scénarios
A chaque fois que le robot prenne une piece de couleur differente, il le depose sur une autre palette.  
    
    
