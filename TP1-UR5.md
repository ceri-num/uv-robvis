# Présentation 
UR5 est un robot à six (6) degré de liberté. Il est constitué des parties suivantes : 
Base, Epaule, Coude, poignet 1, Poignet 2 et Poignet 3.
UR5 est un robot collaboratif avec une charge utile de 5 kg

## Interface de programmation Polyscope

•	Exécuter programme : Permet de choisir et exécuter un programme existant. 
•	Programmer le robot : Modifier un programme ou créer un nouveau programme.
•	Configuration robot : Changer la langue, régler les mots de passe, mettre à jour le logiciel, etc
•	Arrêter le robot : Met le bras du robot hors tension et arrête le boitier contrôleur

Ecran d’initialisation :

Ecran éditeur Pose

Les cases textuelles affichent les valeurs complètes des coordonnées de ce TCP (Tool Centre Point) par rapport à la fonction sélectionnée. X, Y et Z représentent la position de l’outil, tandis que RX, RY et RZ contrôlent l’orientation de l’outil.


Les Différents type de représentation d’orientation de l’outil sont :
•	Le vecteur de rotation [rad] : L’orientation est donnée en vecteur de rotation. La longueur de l’axe est l’angle de pivotement en radians, et le vecteur lui-même donne l’axe autour duquel il faut pivoter.
•	Vecteur de rotation [°] : L’orientation est donnée en vecteur de rotation, ou la longueur du vecteur est l’angle à tourner en degrés.
•	RPY [rad] : Angles Roll, pitch et yaw (RPY), ou les angles sont en radians. La matrice de rotation RPY (rotation X, Y’, Z”) est donnée par :
 
•	Angles RPY [°] Roll, pitch et yaw (RPY), où les angles sont en degrés

Un nouveau programme de robot peut démarrer soit à partir d’un modèle soit à partir d’un programme de robot existant (enregistré).




L’onglet Programme montre le programme actuel en cours d’édition.

Types de déplacement
Il existe trois types de déplacement :
•	DéplacementA (MoveJ) : effectue des déplacements calculés dans l’espace d’articulation du bras du robot. Chaque articulation est contrôlée afin d’atteindre l’emplacement final désiré en même temps. Ce type de déplacement a pour résultat que l’outil suit une trajectoire courbe. Les paramètres partagés qui s’appliquent à ce type de déplacement sont la vitesse d’articulation et l’accélération d’articulation maximales à utiliser pour les calculs du déplacement, spécifiées respectivement en deg/s et deg/s2. Si l’on souhaite que le bras du robot se déplace rapidement entre les points de passage, en ne tenant pas compte de la trajectoire de l’outil entre ces points, ce type de déplacement est le choix préféré.

•	DéplacementL (MoveL) : fait d´déplacer l’outil linéairement entre les points de passage. Cela signifie que chaque articulation effectue un mouvement plus compliqué afin de maintenir l’outil sur une trajectoire en ligne droite. Les paramètres partagés qui peuvent être réglé pour ce type de déplacement sont la vitesse d’outil et l’accélération d’outil désirées, spécifiées respectivement en mm/s et mm/s2, ainsi qu’une fonction. La fonction s´sélectionnée déterminera dans quel espace de fonction sont représentées les positions de l’outil sur les points de passage. Concernant les espaces de fonction, les fonctions variables et les points de passage variables présentent un intérêt particulier. Les fonctions variables peuvent être utilisées lorsqu’il est nécessaire de déterminer la position de l’outil sur un point de passage par la valeur actuelle de la fonction variable lorsque le programme du robot est exécuté.


•	DéplacementP (MoveP) : déplace l’outil linéairement à vitesse constante avec lissages Circulaires, déplacement prévu pour certaines opérations de processus 

Application1 :
Matériel : UR5 et une Boite.
A l’aide de « fonctions » définir un repère « R_boite ». (Suivre le processus de définition de repère) 
Faire un programme UR « TP_2023 » permettant au robot de parcourir les coins de la boite. 
Déplacer la boite mais restant toujours sur le plan de travail.
Déduire le programme pour faire parcourir les mêmes coins de la boite  


Transformation Homogène
Rappel 

Soit (z y x) t les coordonnées d'un point M dans le repère Rj, alors les coordonnées du point M dans le repère Ri,





Application 2 :
Les systèmes de coordonnées :
3 systèmes de coordonnées distincts :
•	Le monde : Système de référence connu.
•	La caméra : Système dans lequel s’effectue la projection des points 3D vers 2D.
•	L’image : Système établissant la référence aux pixels.

Calibration de la caméra
La calibration de la caméra consiste à déterminer les paramètres de la transformation entre les coordonnées du monde et les coordonnées image (et inversement).
2 types de paramètres à prendre en compte
PARAMETRES INTRINSEQUES qui décrivent les propriétés optiques et géométriques internes de la caméra. Transformation projective décrite par les paramètres intrinsèques : Rcamera  Rimage 
PARAMETRES EXTRINSEQUES qui décrivent la relation qui existe entre le référentiel monde et le référentiel Camera. ransformation Rigide décrite par les paramètres extrinsèques (R et T) : Rext  Rcamera
Pour se faire, exécuter le code priseDevue, Calibration et déterminer la matrice RT  

Application 3 :

 

Soit :
bTw la transformation du World dans le repère base du Robot
bTf est la transformation du Flange dans le repère base Robot
fTg est la transformation du Tool(gripper) dans le repère Fange
gTc est la transformation de la Caméra dans le repère Tool
cTw  est la transformation du World dans le repère Camera

Détermination de bTw
Soit un R1 une base associée à la mire de calibration. Soit R0, le repère associé au robot.  

1.	Définir trois points A, B et tels que ABC soit un trièdre rectangle direct (AB, AC, AB^AC) soit une base directe.
2.	 Trouver la matrice de transformation entre le repère R1 ((AB, AC, AB^AC)) et le repère R0 du robot. En déduire la transformation homogène T01 entre R0 et R1.


Comment utiliser les informations de la caméra pour amener le Tool vers un point spécifique ?
Déterminer le gTc la transformation de la Caméra dans le repère Tool 
Sachant :
```
bTw  = gTf* fTb* bTw
bTw  = gTc* cTw
gTc  = gTf* fTb* bTw*inv(cTw)
```



Déduire la transformation qui permet de d’exprimer tout point du repère camera dans le repère base du robot 

Placer un cube jaune dans l’espace de travail puis exécuter le code de détection 
Trouver les coordonnées du centre du cube dans le repère robot.

# Detection reconnaissance et localisation d'objet 


# [Detection](https://www.aranacorp.com/fr/reconnaissance-de-forme-et-de-couleur-avec-python/amp/)
Nous allons créer un classe détection de forme qui va nous permettre de sélectionner une forme en fonction du nombre de contours trouvé.
Soit une classe python ``class Detector`` avec les fonctions:
- ``jaune``:image
-  ``vert``:image
- ``rouge``:image
-  ``bleu``: image
-  ``contours`` : image
- ``forme`` : contours
-  ``centre```: contours


## Detection de couleur 
``` python

# read image
bgr_img = cv2.imread("image.png")
# Convert HSV
hsv_img = cv2.cvtColor(bgr_img, cv2.COLOR_BGR2HSV)

# Lower and higher HSV value for red color
def blue_hsv():
    # H -> 40 -70
    # S -> 150-255
    # V -> 20-255
    
    # define range of blue color in HSV
    lower_hsv = np.array([110, 50, 50])
    higher_hsv = np.array([130, 255, 255])
    
    # generating mask for green color
    mask = cv2.inRange(hsv_img, lower_hsv, higher_hsv)
    return mask


mask = blue_hsv()

detected_img = cv2.bitwise_and(bgr_img, bgr_img, mask= mask)
cv2.imshow("detected image", detected_img)
cv2.waitKey(0)

```
 les limites: 
Bleu: 
 H -> 10 
 S -> 175-255
 V -> 20-255
Jaunes:
 H -> 10 
 S -> 175-255
 V -> 20-255
vert:
 H -> 10 
 S -> 175-255
 V -> 20-255
1. Ecrire les fonctions des mask du rouge, du jaune, du vert 
2. A Partir de l'image `` ecrire programme pour classer les figures en fonction de leur couleur``

Realsense
``` python
import cv2
import numpy as np

cap = cv2.VideoCapture(0)

while(1):

    # Take each frame
    _, frame = cap.read()

    # Convert BGR to HSV
    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)

    # define range of blue color in HSV
    lower_blue = np.array([110,50,50])
    upper_blue = np.array([130,255,255])

    # Threshold the HSV image to get only blue colors
    mask = cv2.inRange(hsv, lower_blue, upper_blue)

    # Bitwise-AND mask and original image
    res = cv2.bitwise_and(frame,frame, mask= mask)

    cv2.imshow('frame',frame)
    cv2.imshow('mask',mask)
    cv2.imshow('res',res)
    k = cv2.waitKey(5) & 0xFF
    if k == 27:
        break

cv2.destroyAllWindows()
```

On prendre une camera sur le robot. utliser cette camera pour reconnaitre 
et classer les pieces en fonction de leur couleur

## Detection de formes: 
``` python

def prisePhoto(n=0):

    camera = cv.VideoCapture(n, cv2.CAP_DSHOW)

    ret, img = camera.read()

    # img = cv.imread("img11.jpg")

    # Was the image there?
    if img is None:
        print("Error: File not found")
        exit(0)

    cv.imshow('Input Image', img)

    # Convert image to grayscale
    gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

    # Convert image to binary
    _, bw = cv.threshold(gray, 50, 255, cv.THRESH_BINARY | cv.THRESH_OTSU)

    # Find all the contours in the thresholded image
    contours, _ = cv.findContours(bw, cv.RETR_LIST, cv.CHAIN_APPROX_NONE)

    detection=[]

    for i, c in enumerate(contours):

             # Calculate the area of each contour
             area = cv.contourArea(c)

             # Ignore contours that are too small or too large
             if area < 3700 or 200000 < area:
                 continue
             centre,angles = axes(c, img)
             detection.append(axes(c, img))

    # print(detection)

    cv.imshow('Image', img)
    cv.waitKey(0)
    cv.destroyAllWindows()


    # Save the output image to the current directory
    cv.imwrite("img.jpg", img)
    return detection

```
Ecrire un programme pour detecter les contoures et les centres de chaque pieces  

## Centre : 

# Localisation d'un objet

## Calibration 

### Prise de vue 

### Calibration HandEye

### Prise d'un objet 


# Calibration

## PriseDeVueRobot

Creer un fichier ``PriseDeVueRobot.py`` dans le repertoire ``Calibration``
Le but c'est d'écrire un programe Python pour capturer les images d'une mire de calibration :
1. Calcul et Enregistrement des T_gripper2base à partir des poses de prise de vue dans le dossier T_gripper2base
2. Enregistrement des poistions et l'orientation des positions de prise de vue dans le dossier JointPositions
3. Enregistrement des images de la mire de calibration dans le repertoire RGBImgs

## CalibrateHandEye

Creer un fichier ``CalibrateHandEye.py`` dans le repertoire ``Calibration``
CalibrateHandEye() permet de determiner la transformation Camera dans le repere de l'outil. 
Paramètres d'initialisation: la mire de la calibration est 7X9 de 20 mm
Charger les images et les transformation de gripper dans la base: T_gripper2base
Calcul des matrices intrinseques et extrinseques: T_mtx, T_target2Cam
Calibration hand-eye calibration permet de determiner la transformation T_cam2gripper
``cv.calibrateHandEye(R_target2cam, t_target2cam, R_gripper2base, t_gripper2base)``

## Estimation de Pose
Creer un fichier ``prisePiece.py`` dans le repertoire ``Calibration``
Pour chaque T_cam2gripper des methode calibrateHandEye: 
pour chaque T_cam2gripper des methodes ``cv.calibrateHandEye``, écrire un programme d'estimation de pose (X, Y, Z) à partir des coordonnées d'un point pixel (x, y) d'une image prise à une pose ``posePrise``, 
Comparer les differentes methode de calcul de calibrateHandEye

