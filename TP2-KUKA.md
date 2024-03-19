
## Introduction


## Materiels
Les materiels à votre disposition sont:
- robot kuka R650 avec une pince
- kit vision composé d'une realsense D435i 
- PC vision où seront lancer les noeuds de camera realsense
- PC fixe pour la programmeation en python sous vscode
- les cubes de differentes couleurs: jaune, vert, bleu et rouge
- les Palettes A, B et C

## Logiciel
Le robot communique avec le PC fixe en liaison serie. Un environnement ROS2 est conçu pour la programmation du robot en python avec un environnement virtuel
Dans l'espace de travail de ROS2 est doté des noeuds:
- ros2_aruco : permet de lancer noeud de lecture d'aruco code
- ros2_interfaces: contenant les interfaces message
- service: permet de lancer un service de detection de couleur à partir de l'id de l'aruco_code
- robot: contient l'excutable de la base de données et le programme robot.
  
## Configuration
Ouvrir les terminaux:
### PC portable
- terminal 1
```python
cd ~/Ros_ws
```
Sourcer votre environnement:
```python
source install/setup.bash
```
Lancement du noeud de la camera realsense 
```python
ros2 launch realsense2_camera rs_launch.py
```
- terminal 2
Lancer le noeud aruco
```python
ros2 launch ros2_aruco aruco_recognition.launch.py 
```
- terminal 3
  
  Faire les memes procedures
service client
```python
ros2 run service service_client
```


### PC fixe
- terminal 1
```python
cd ~/Ros_ws
```
Activation de l'environnement virtuel 
```python
source ./venv/bin/activate
```
En sortie vous aurez:
```python
(venv) robot@PC-41496:~/Ros_ws$ 
```
Sourcer votre environnement:
```python
source install/setup.bash
```
Lancement du noeud service qui permet de determiner la couleur d'une piece:
service serveur 
```python
ros2 launch service add_color_check.launch.py 
```

- terminal 2 : vscode

Avant d'executer un code modifier, il faut reconstruire le package par:
```python
colcon build --packages-select robot
```

- terminal 3
Passer en mode admin pour executer votre code
Mode admin
```python
(venv) root@PC-41496:/home/robot/Ros_ws#
```
```python
source install/setup.bash
```
lancer votre noeud
```python
ros2 run robot kuka.py 
```
## Prise en main
kuka: dispose des fonctions principales suivantes: 


### Tester votre premier programme en python
```
#!/usr/bin/env python3
from pykuka.pykuka import Pose
import pykuka.pykuka as kuka
import pykuka.transformations as tf
import time
import database as database

# initialisation et connexion au robot 
kuka.initialize("/dev/ttyS0")

base= {"base":"Base","BaseBleu":"BaseBleu","BaseRouge":"BaseRouge","BaseGrise":"BaseGrise","BaseVert":"BaseVert"}
db = database.Database(filename = 'data.db', table = 'PIECE')
pose = {"id": 3, "couleur":"rouge", "x":6.0, "y": 9.0, "z": 1.0, "a":2.0 , "b":0.0, "c": 0.0, "longueur":0.0, "largeur": 0.0, "hauteur":0.0, "poste":0.0, "frame":"BaseBleu", "rapport":"none"}
# db.updateAll(9,pose)
db.record_data(pose)
pos=db.readColor(3)
print(db.readIDColor(3))
# deplaclent relatif sur l'axe x
kuka.move_linRel(10.0,0.0,0.0,0.0,0.0,0.0)
# Ouvrir la pince 
kuka.open_tool()
# Fermer la pince 
kuka.close_tool()
```
## Depalcement 

## Travail à faire

scenarios 
Soint les points Pi(0<i<N) de la Pallette, P0 le point de depart, pPrise position de prise, pPose la position de depose, pAvant,pApres les position respectivment 
avant et apres la prise de piece sur le convoyeurs, pa les positions d'approche, px les positions de depose de pieces sur la palette,
soient Dx,DY et DZ la distances entre les positions suivant respectivement les axes x,y et z

1. Apprendre des points Pi(0<i<N) des Pallettes A, B, C .
  Ecrire un programme correspondant au robot de prendre les pieces sur le convoyeur et les poser sur les pallette A
Deduire l'algorithme qui permet de faire la meme operation connaissant les points seulement les positions P0 et P1


![Pallete Jaune](./Imgs/J1.jpeg)  ![Pallete Jaune](./Imgs/Jaune.jpeg)

   
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
    
    
