# ROS 2 kuka 650

# Matériel 

-  kuka 650
- Camera Realsense
- Les pièces
  
# Sujet 
Dans le cadre de ce projet, il s'agira de faire le tri par scan et la palettisation des pièces conforme et selon la couleur .
Les phases du projet seront les suivantes : 
1.  Conception du système d'identification de la pièces avec la camera realsense:
  - identification par aruco code,
  - détermination de couleur
  - détermination de dimension de la pièce
  
  - rapport scan: conforme ou non conforme
2. Prise de pièces sur convoyeur, faire scan et faire rapport de conformité selon la dimension :
 - rapport scan: conforme ou non conforme
 - écrire le rapport dans une base de donne

# Livrable 
structure des packages ros2


``` python
ros2_ws/
      robot/ 
      		src/
      			kuka(integration) (detection, localisation, trajectoire et prise) 
      	vision/	
      		src/
      			realsense1 fixe( integration) 
      			realsense2 mobile(integration)
      	database/
      		src/
      			sqldatabase
	

  ```

- Package ros2 et le code fonctionnel 
- Une vidéo du fonctionnement
  



